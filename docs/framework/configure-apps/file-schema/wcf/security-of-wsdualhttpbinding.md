---
title: <security> de <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: 4969c041678bbf3490975bc0ec53507b6cf762bb
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738611"
---
# <a name="security-of-wsdualhttpbinding"></a>\<> de segurança do \<wsDualHttpBinding >
Define os recursos de segurança do [> de\<WSDualHttpBinding](wsdualhttpbinding.md).  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsDualHttpBinding >** ](wsdualhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**security >**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|modo|Adicional. Especifica o tipo de segurança que é aplicado. O valor padrão é `Message`. Este atributo é do tipo <xref:System.ServiceModel.WSDualHttpSecurityMode>.|  
  
## <a name="mode-attribute"></a>Atributo de modo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Nenhum|A segurança é desabilitada.|  
|Mensagem|A segurança é fornecida usando a segurança de mensagem SOAP.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<message >](message-of-wsdualhttpbinding.md)|Define as configurações para a segurança em nível de mensagem. Este elemento é do tipo <xref:System.ServiceModel.MessageSecurityOverHttp>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<binding >](bindings.md)|Define todos os recursos de associação do [\<wsDualHttpBinding >](wsdualhttpbinding.md).|  
  
## <a name="remarks"></a>Comentários  
 Uma associação dupla expõe o endereço IP do cliente para o serviço. O cliente deve usar a segurança para garantir que ele se conecte apenas aos serviços que confia.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [Protegendo serviços e clientes](../../../wcf/feature-details/securing-services-and-clients.md)
- [Associações](../../../wcf/bindings.md)
- [Configurando associações fornecidas pelo sistema](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Usando associações para configurar serviços e clientes](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding >](bindings.md)
