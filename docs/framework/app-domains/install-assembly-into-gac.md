---
title: Como instalar um assembly no cache de assembly global
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
ms.openlocfilehash: 64878a795a7c5b790c8991064e32b82505685c0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155557"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Como instalar um assembly no cache de assembly global

O cache de assembly global armazena os assemblies que vários aplicativos compartilham. Instale um assembly no [cache de assembly global](gac.md) com um dos seguintes componentes:

- [Instalador do Windows](#windows-installer)
- [Ferramenta Global Assembly Cache](#global-assembly-cache-tool)

> [!IMPORTANT]
> Você pode instalar apenas conjuntos com nome forte no cache de montagem global. Para obter informações sobre como criar um conjunto com nome forte, consulte [Como: Assinar uma montagem com um nome forte](../../standard/assembly/sign-strong-name.md).

## <a name="windows-installer"></a>Windows Installer

[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), o mecanismo de instalação do Windows, é a maneira recomendada de adicionar assemblies ao cache de assembly global. O Windows Installer fornece uma contagem de referências de assemblies no cache de assembly global e outros benefícios. Para criar um pacote do instalador do Windows Installer, use a [extensão de conjunto de ferramentas WiX do Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

## <a name="global-assembly-cache-tool"></a>Ferramenta Cache de Assembly Global

Você pode usar o [utilitário .NET Global Assembly Cache (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) para adicionar montagens ao cache de montagem global e visualizar o conteúdo do cache de montagem global.

   > [!NOTE]
   > O *gacutil.exe* é indicado apenas para fins de desenvolvimento. Não o use para instalar assemblies de produção no cache de assembly global.

A sintaxe para usar o *gacutil.exe* para instalar um assembly no cache de assembly global é a seguinte:

```cmd
gacutil -i <assembly name>
```

Neste comando, * \<o nome de montagem>* é o nome do conjunto a ser instalado no cache de montagem global.

Se *gacutil.exe* não estiver no caminho do sistema, use o [prompt de comando do Desenvolvedor para>de * \<versão *VS ](../tools/developer-command-prompt-for-vs.md).

O exemplo a seguir instala um assembly com o nome do arquivo *hello.dll* no cache de assembly global.

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> Nas versões anteriores do .NET Framework, a extensão do shell do Windows *Shfusion.dll* permitia a instalação de assemblies arrastando-os no Explorador de Arquivos. Começando no .NET Framework 4, a *Shfusion.dll* ficou obsoleta.

## <a name="see-also"></a>Confira também

- [Trabalhe com montagens e o cache de montagem global](working-with-assemblies-and-the-gac.md)
- [Como: Remover uma montagem do cache de montagem global](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil.exe (ferramenta Global Assembly Cache)](../tools/gacutil-exe-gac-tool.md)
- [Como: Assinar uma assembléia com um nome forte](../../standard/assembly/sign-strong-name.md)
