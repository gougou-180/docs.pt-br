---
title: Investigação padrão-.NET Core
description: Visão geral da lógica de <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> investigação do .NET Core para localizar dependências.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 020b1d0342ae822021905d2e749037f45031eb22
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70234644"
---
# <a name="default-probing"></a><span data-ttu-id="7701e-103">Investigação padrão</span><span class="sxs-lookup"><span data-stu-id="7701e-103">Default probing</span></span>

<span data-ttu-id="7701e-104">A <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instância é responsável por localizar as dependências de um assembly.</span><span class="sxs-lookup"><span data-stu-id="7701e-104">The <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance is responsible for locating an assembly's dependencies.</span></span> <span data-ttu-id="7701e-105">Este artigo descreve a <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> lógica de investigação da instância.</span><span class="sxs-lookup"><span data-stu-id="7701e-105">This article describes the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance's probing logic.</span></span>

## <a name="host-configured-probing-properties"></a><span data-ttu-id="7701e-106">Propriedades de investigação configuradas pelo host</span><span class="sxs-lookup"><span data-stu-id="7701e-106">Host configured probing properties</span></span>

<span data-ttu-id="7701e-107">Quando o tempo de execução é iniciado, o host de tempo de execução fornece um conjunto de propriedades <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> de investigação nomeadas que configuram caminhos de investigação.</span><span class="sxs-lookup"><span data-stu-id="7701e-107">When the runtime is started, the runtime host provides a set of named probing properties that configure <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> probe paths.</span></span>

<span data-ttu-id="7701e-108">Cada propriedade de investigação é opcional.</span><span class="sxs-lookup"><span data-stu-id="7701e-108">Each probing property is optional.</span></span>  <span data-ttu-id="7701e-109">Se houver, cada propriedade será um valor de cadeia de caracteres que contém uma lista delimitada de caminhos absolutos.</span><span class="sxs-lookup"><span data-stu-id="7701e-109">If present, each property is a string value that contains a delimited list of absolute paths.</span></span> <span data-ttu-id="7701e-110">O delimitador é '; ' no Windows e ': ' em todas as outras plataformas.</span><span class="sxs-lookup"><span data-stu-id="7701e-110">The delimiter is ';' on Windows and ':' on all other platforms.</span></span>

|<span data-ttu-id="7701e-111">Nome da Propriedade</span><span class="sxs-lookup"><span data-stu-id="7701e-111">Property Name</span></span>                 |<span data-ttu-id="7701e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="7701e-112">Description</span></span>  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | <span data-ttu-id="7701e-113">Lista de caminhos de arquivo de assembly de aplicativo e plataforma.</span><span class="sxs-lookup"><span data-stu-id="7701e-113">List of platform and application assembly file paths.</span></span> |
|`PLATFORM_RESOURCE_ROOTS`       | <span data-ttu-id="7701e-114">Lista de caminhos de diretório para pesquisar por assemblies de recurso satélite.</span><span class="sxs-lookup"><span data-stu-id="7701e-114">List of directory paths to search for satellite resource assemblies.</span></span> |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | <span data-ttu-id="7701e-115">Lista de caminhos de diretório para pesquisar bibliotecas não gerenciadas (nativas).</span><span class="sxs-lookup"><span data-stu-id="7701e-115">List of directory paths to search for unmanaged (native) libraries.</span></span>        |
|`APP_PATHS`                     | <span data-ttu-id="7701e-116">Lista de caminhos de diretório para pesquisar assemblies gerenciados</span><span class="sxs-lookup"><span data-stu-id="7701e-116">List of directory paths to search for managed assemblies</span></span> |
|`APP_NI_PATHS`                  | <span data-ttu-id="7701e-117">Lista de caminhos de diretório para pesquisar imagens nativas de assemblies gerenciados.</span><span class="sxs-lookup"><span data-stu-id="7701e-117">List of directory paths to search for native images of managed assemblies.</span></span> |

### <a name="how-are-the-properties-populated"></a><span data-ttu-id="7701e-118">Como as propriedades são populadas?</span><span class="sxs-lookup"><span data-stu-id="7701e-118">How are the properties populated?</span></span>

<span data-ttu-id="7701e-119">Há dois cenários principais para popular as propriedades dependendo se o `<myapp>.deps.json` arquivo existe.</span><span class="sxs-lookup"><span data-stu-id="7701e-119">There are two main scenarios for populating the properties depending on whether the `<myapp>.deps.json` file exists.</span></span>

- <span data-ttu-id="7701e-120">Quando o `*.deps.json` arquivo estiver presente, ele será analisado para preencher as propriedades de investigação.</span><span class="sxs-lookup"><span data-stu-id="7701e-120">When the `*.deps.json` file is present, it's parsed to populate the probing properties.</span></span>
- <span data-ttu-id="7701e-121">Quando o `*.deps.json` arquivo não está presente, supõe-se que o diretório do aplicativo contenha todas as dependências.</span><span class="sxs-lookup"><span data-stu-id="7701e-121">When the `*.deps.json` file isn't present, the application's directory is assumed to contain all the dependencies.</span></span> <span data-ttu-id="7701e-122">O conteúdo do diretório é usado para preencher as propriedades de investigação.</span><span class="sxs-lookup"><span data-stu-id="7701e-122">The directory's contents are used to populate the probing properties.</span></span>

<span data-ttu-id="7701e-123">Além disso, `*.deps.json` os arquivos para todas as estruturas referenciadas são analisados de forma semelhante.</span><span class="sxs-lookup"><span data-stu-id="7701e-123">Additionally, the `*.deps.json` files for any referenced frameworks are similarly parsed.</span></span>

<span data-ttu-id="7701e-124">Por fim, a `ADDITIONAL_DEPS` variável de ambiente pode ser usada para adicionar outras dependências.</span><span class="sxs-lookup"><span data-stu-id="7701e-124">Finally the environment variable `ADDITIONAL_DEPS` can be used to add additional dependencies.</span></span>

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a><span data-ttu-id="7701e-125">Como fazer ver as propriedades de investigação do código gerenciado?</span><span class="sxs-lookup"><span data-stu-id="7701e-125">How do I see the probing properties from managed code?</span></span>

<span data-ttu-id="7701e-126">Cada propriedade está disponível chamando a <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> função com o nome da propriedade da tabela acima.</span><span class="sxs-lookup"><span data-stu-id="7701e-126">Each property is available by calling the <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> function with the property name from the table above.</span></span>

### <a name="how-do-i-debug-the-probing-properties-construction"></a><span data-ttu-id="7701e-127">Como fazer depurar a construção das propriedades de investigação?</span><span class="sxs-lookup"><span data-stu-id="7701e-127">How do I debug the probing properties' construction?</span></span>

<span data-ttu-id="7701e-128">O host de tempo de execução do .NET Core produzirá mensagens de rastreamento úteis quando determinadas variáveis de ambiente estiverem habilitadas:</span><span class="sxs-lookup"><span data-stu-id="7701e-128">The .NET Core runtime host will output useful trace messages when certain environment variables are enabled:</span></span>

|<span data-ttu-id="7701e-129">Variável de ambiente</span><span class="sxs-lookup"><span data-stu-id="7701e-129">Environment Variable</span></span>        |<span data-ttu-id="7701e-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="7701e-130">Description</span></span>  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |<span data-ttu-id="7701e-131">Habilita o rastreamento.</span><span class="sxs-lookup"><span data-stu-id="7701e-131">Enables tracing.</span></span>|
|`COREHOST_TRACEFILE=<path>` |<span data-ttu-id="7701e-132">Rastreia um caminho de arquivo em vez do padrão `stderr`.</span><span class="sxs-lookup"><span data-stu-id="7701e-132">Traces to a file path instead of the default `stderr`.</span></span>|
|`COREHOST_TRACE_VERBOSITY`  |<span data-ttu-id="7701e-133">Define o detalhamento de 1 (menor) para 4 (mais alto).</span><span class="sxs-lookup"><span data-stu-id="7701e-133">Sets the verbosity from 1 (lowest) to 4 (highest).</span></span>|

## <a name="managed-assembly-default-probing"></a><span data-ttu-id="7701e-134">Investigação padrão do assembly gerenciado</span><span class="sxs-lookup"><span data-stu-id="7701e-134">Managed assembly default probing</span></span>

<span data-ttu-id="7701e-135">Ao investigar para localizar um assembly gerenciado, o <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> procura na ordem em:</span><span class="sxs-lookup"><span data-stu-id="7701e-135">When probing to locate a managed assembly, the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> looks in order at:</span></span>
- <span data-ttu-id="7701e-136">Arquivos que correspondem <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> ao `TRUSTED_PLATFORM_ASSEMBLIES` (após a remoção de extensões de arquivo).</span><span class="sxs-lookup"><span data-stu-id="7701e-136">Files matching the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> in `TRUSTED_PLATFORM_ASSEMBLIES` (after removing file extensions).</span></span>
- <span data-ttu-id="7701e-137">Arquivos de assembly de imagem `APP_NI_PATHS` nativa no com extensões de arquivo comuns.</span><span class="sxs-lookup"><span data-stu-id="7701e-137">Native image assembly files in `APP_NI_PATHS` with common file extensions.</span></span>
- <span data-ttu-id="7701e-138">Arquivos de assembly `APP_PATHS` no com extensões de arquivo comuns.</span><span class="sxs-lookup"><span data-stu-id="7701e-138">Assembly files in `APP_PATHS` with common file extensions.</span></span>

## <a name="satellite-resource-assembly-probing"></a><span data-ttu-id="7701e-139">Investigação de assembly satélite (recurso)</span><span class="sxs-lookup"><span data-stu-id="7701e-139">Satellite (resource) assembly probing</span></span>

<span data-ttu-id="7701e-140">Para localizar um assembly satélite para uma cultura específica, construa um conjunto de caminhos de arquivo.</span><span class="sxs-lookup"><span data-stu-id="7701e-140">To find a satellite assembly for a specific culture, construct a set of file paths.</span></span>

<span data-ttu-id="7701e-141">Para cada caminho no `PLATFORM_RESOURCE_ROOTS` e, `APP_PATHS`em seguida, <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> acrescente a cadeia de caracteres, um <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> separador de diretório, a cadeia de caracteres e a extensão '. dll '.</span><span class="sxs-lookup"><span data-stu-id="7701e-141">For each path in `PLATFORM_RESOURCE_ROOTS` and then `APP_PATHS`, append the <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> string, a directory separator, the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> string, and the extension '.dll'.</span></span>

<span data-ttu-id="7701e-142">Se existir algum arquivo correspondente, tente carregá-lo e retorná-lo.</span><span class="sxs-lookup"><span data-stu-id="7701e-142">If any matching file exists, attempt to load and return it.</span></span>

## <a name="unmanaged-native-library-probing"></a><span data-ttu-id="7701e-143">Investigação de biblioteca não gerenciada (nativa)</span><span class="sxs-lookup"><span data-stu-id="7701e-143">Unmanaged (native) library probing</span></span>

<span data-ttu-id="7701e-144">Ao investigar para localizar uma biblioteca não gerenciada, o `NATIVE_DLL_SEARCH_DIRECTORIES` é pesquisado procurando por uma biblioteca correspondente,</span><span class="sxs-lookup"><span data-stu-id="7701e-144">When probing to locate an unmanaged library, the `NATIVE_DLL_SEARCH_DIRECTORIES` are searched looking for a matching library,</span></span>