---
title: elemento <add> para NameValueSectionHandler e DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
ms.openlocfilehash: 57722f3518fad12cb8e6e35d68f40bb8465bdd86
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215436"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<Adicionar > elemento para NameValueSectionHandler e DictionarySectionHandler

Adiciona configurações de aplicativo personalizadas. Cada **\<adicionar >** marca contém um par chave/valor.

[ **\<configuration>** ](configuration-element.md)\
&nbsp;&nbsp;[ **\<sectionname >** ](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<adicionar >**

## <a name="syntax"></a>Sintaxe

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a>Atributos

| Atributo | DESCRIÇÃO |
| --------- | ----------- |
| **chave**   | Atributo obrigatório.<br><br>Especifica o nome da configuração. |
| **value** | Atributo obrigatório.<br><br>Especifica o valor da configuração. |

## <a name="parent-element"></a>Elemento pai

| Elemento | DESCRIÇÃO |
| ------- | ------------|
| [ **\<sectionname >** Elementos](custom-element-2.md) | Define as configurações para seções de configuração personalizadas que usam as classes <xref:System.Configuration.NameValueSectionHandler> e <xref:System.Configuration.DictionarySectionHandler>. |

## <a name="child-elements"></a>Elementos filho

Nenhum

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como definir uma seção de configuração personalizada e usar o **\<adicionar >** elemento para colocar as configurações na seção:

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
</configuration>
```

## <a name="configuration-file"></a>Arquivo de configuração

Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.

## <a name="see-also"></a>Confira também

- [Esquema do arquivo de configuração para o .NET Framework](index.md)
