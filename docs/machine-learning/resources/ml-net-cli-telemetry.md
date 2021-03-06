---
title: Coleta de telemetria pela CLI do ML.NET
description: Conheça os recursos de telemetria da CLI do ML.NET que coletam informações de uso para análise, quais dados são coletados e como desabilitá-los. Além disso, encontre links para o contrato de licença do .NET e informações sobre a conformidade com o RGPD da Microsoft.
ms.topic: conceptual
ms.date: 09/03/2019
ms.custom: mlnet-tooling
ms.openlocfilehash: 99e11acba343cc689c3219ca9316144fc62cd618
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78849738"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a>Coleta de telemetria pela CLI do ML.NET

A [CLI do ML.NET](https://aka.ms/mlnet-cli) inclui um recurso de telemetria que coleta dados anônimos de uso que são agregados para uso pela Microsoft.

## <a name="how-microsoft-uses-the-data"></a>Como a Microsoft usa os dados

A equipe de produto usa dados de telemetria do ML.NET CLI para ajudar a entender como melhorar as ferramentas. Por exemplo, se os clientes usarem com pouca frequência uma determinada tarefa de aprendizado de máquina, a equipe de produto investigará por que e usará as descobertas para priorizar o desenvolvimento de recursos. A telemetria da CLI do ML.NET também ajuda com a depuração de problemas, como falhas e anomalias de código.

Embora a equipe de produto aprecia essas informações, ela também sabe que nem todo mundo deseja enviá-las. [Saiba como desabilitar a telemetria.](#opt-out-of-data-collection)

## <a name="scope"></a>Escopo

O comando `mlnet` inicia a CLI do ML.NET, mas o comando em si não coleta telemetria.

A telemetria *não está habilitada* quando você executa o `mlnet` sem outro comando anexado. Por exemplo: 

- `mlnet`
- `mlnet --help`

A telemetria *está habilitado* quando você executa um [comando da CLI do ML.NET](../reference/ml-net-cli-reference.md), como `mlnet auto-train`.

## <a name="opt-out-of-data-collection"></a>Recusar a coleta de dados

O recurso de telemetria da CLI do ML.NET Core está habilitado por padrão.

Recuse o recurso de telemetria configurando a variável de ambiente `MLDOTNET_CLI_TELEMETRY_OPTOUT` como `1` ou `true`. Essa variável de ambiente aplica-se globalmente à ferramenta CLI ML.NET.

## <a name="data-points-collected"></a>Pontos de dados coletados

O recurso coleta os seguintes dados:

- Qual comando foi invocado, como `auto-train`
- Nomes de parâmetros de linha de comando usados (ou seja, "nome do conjunto de dados, nome da coluna de rótulo, tarefa ml, caminho de saída, tempo máximo de exploração, verbosidade")
- Endereço MAC com hash: uma ID única e criptograficamente anônima (SHA256) para um computador
- Carimbo de data/hora de uma invocação
- Três endereços IP de octeto (não um endereço IP completo) usados apenas para determinar a localização geográfica
- Nome de todos os argumentos/parâmetros usados. Não valores do cliente, como cadeias de caracteres
- Nome do arquivo de conjunto de dados com hash
- Bucket do tamanho do arquivo de conjunto de dados
- Sistema operacional e versão
- Valor do --parâmetro da tarefa: `regression`Valores categóricos, tais como , `binary-classification`e`multiclass-classification`
- ML.NET versão CLI (ou seja, 0.3.27703.4)

Os dados são enviados com segurança para os servidores Microsoft usando a tecnologia [Azure Application Insights](https://azure.microsoft.com/services/application-insights/), mantidos em acesso restrito e usados sob controles de segurança rigorosos dos sistemas do [Armazenamento do Microsoft Azure](https://azure.microsoft.com/services/storage/) seguros.

### <a name="data-points-not-collected"></a>Pontos de dados não coletados

O recurso de telemetria *não* coleta:

- dados pessoais, como nomes de usuário
- nomes de arquivo de conjunto de dados
- dados de arquivos de conjunto de dados

Se você suspeita que a telemetria da CLI do ML.NET está coletando dados confidenciais ou que os dados estão sendo manipulados de modo inseguro ou inadequado, registre um problema no repositório [ML.NET](https://github.com/dotnet/machinelearning) para investigação.

## <a name="license"></a>Licença

A distribuição microsoft de ML.NET CLI é licenciada com os [Termos de Licença de Software da Microsoft: Microsoft .NET Library](https://aka.ms/dotnet-core-eula). Para obter detalhes sobre a coleta e o processamento de dados, veja a seção intitulada "Dados".

## <a name="disclosure"></a>Divulgação

Quando você executar pela primeira vez um [comando da CLI do ML.NET](../reference/ml-net-cli-reference.md), como `mlnet auto-train`, a ferramenta da CLI do ML.NET exibe o texto de divulgação que informa como recusar a telemetria. O texto pode variar um pouco dependendo da versão da CLI que você está executando.

## <a name="see-also"></a>Confira também

- [Referência da CLI do ML.NET](../reference/ml-net-cli-reference.md)
- [Termos da licença de software da Microsoft: Biblioteca Microsoft .NET](https://aka.ms/dotnet-core-eula)
- [Privacidade na Microsoft](https://www.microsoft.com/trustcenter/privacy/)
- [Política de Privacidade da Microsoft](https://privacy.microsoft.com/privacystatement)
