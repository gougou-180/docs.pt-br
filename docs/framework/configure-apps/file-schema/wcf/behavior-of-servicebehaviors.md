---
title: <behavior> de <serviceBehaviors>
ms.date: 03/30/2017
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
ms.openlocfilehash: 115f94fc3f17dc5b4dd1ee3a090f2c9d121f810b
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74139725"
---
# <a name="behavior-of-servicebehaviors"></a>comportamento de \<> de \<percomportamentos >
O `behavior` elemento contém uma coleção de configurações para o comportamento de um serviço. Cada comportamento é indexado pela sua `name`. Os serviços podem vincular a cada comportamento por meio desse nome usando o atributo `behaviorConfiguration` do elemento [ponto de extremidade\<](endpoint-element.md) . Isso permite que os pontos de extremidade compartilhem configurações comuns de comportamento sem redefinir as configurações. A partir do .NET Framework 4, associações e comportamentos não precisam ter um nome. Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).  
  
> [!NOTE]
> Elementos de comportamento específicos das atividades de fluxo de trabalho do Windows, como o elemento [\<sendMessageChannelCache >](../windows-workflow-foundation/sendmessagechannelcache.md) , são documentados no [comportamento de\<> da](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) página \<de trabalho.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;\<[**comportamentos**](behaviors.md) >
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](servicebehaviors.md) >
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**comportamento >**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <serviceBehaviors>
       <behavior name="String" />
    </serviceBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|name|Uma cadeia de caracteres exclusiva que contém o nome da configuração do comportamento. Esse valor é uma cadeia de caracteres definida pelo usuário que deve ser exclusiva, pois ele atua como a cadeia de caracteres de identificação para o elemento. A partir do .NET Framework 4, associações e comportamentos não precisam ter um nome. Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<dataContractSerializer >](datacontractserializer-element.md)|Contém dados de configuração para o DataContractSerializer.|  
|[\<PersistenceProvider >](persistenceprovider.md)|Especifica o tipo da implementação do provedor de persistência a ser usado, bem como o tempo limite a ser usado para operações de persistência.|  
|[> de roteamento de \<](routing-of-servicebehavior.md)|Fornece acesso de tempo de execução ao serviço de roteamento para permitir a modificação dinâmica da configuração de roteamento.|  
|[\<> de autenticação](serviceauthenticationmanager.md)|Fornece um elemento de configuração de fluxo de trabalho que estabelece no nível de serviço a validade de uma transmissão, mensagem ou originador.|  
|[> de \<de autorização](serviceauthorization-element.md)|Especifica as configurações que autorizam o acesso às operações de serviço.|  
|[\<serviceCredentials >](servicecredentials.md)|Especifica a credencial a ser usada na autenticação do serviço e nas configurações relacionadas à validação da credencial do cliente.|  
|[> de \<do indebug](servicedebug.md)|Especifica recursos de depuração e de informações de ajuda para um serviço Windows Communication Foundation (WCF).|  
|[> de \<de descoberta](servicediscovery.md)|Especifica a descoberta de pontos de extremidade de serviço.|  
|[> de \<de metadados](servicemetadata.md)|Especifica a publicação de metadados de serviço e informações associadas.|  
|[\<serviceSecurityAudit >](servicesecurityaudit.md)|Especifica as configurações que habilitam a auditoria de eventos de segurança durante operações de serviço.|  
|[> de \<perthrottling](servicethrottling.md)|Especifica o mecanismo de limitação de um serviço WCF.|  
|[> de \<de tempo limite](servicetimeouts.md)|Especifica o tempo limite para um serviço.|  
|[> \<workflowRuntime](workflowruntime.md)|Especifica as configurações para uma instância de WorkflowRuntime para hospedar serviços WCF baseados em fluxo de trabalho.|  
|[\<useRequestHeadersForMetadataAddress >](userequestheadersformetadataaddress.md)|Habilita a recuperação de informações de endereço de metadados dos cabeçalhos de mensagem de solicitação.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[> de \<de portais](servicebehaviors.md)|Uma coleção de elementos de comportamento de serviço.|
