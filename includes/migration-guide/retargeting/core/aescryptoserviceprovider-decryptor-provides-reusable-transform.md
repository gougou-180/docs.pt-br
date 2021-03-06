---
ms.openlocfilehash: c008809606372c84b05a2facd1cac1293382aed4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859336"
---
### <a name="aescryptoserviceprovider-decryptor-provides-a-reusable-transform"></a>Descriptografador AesCryptoServiceProvider fornece uma transformação reutilizável

|   |   |
|---|---|
|Detalhes|Começando com aplicativos destinados ao .NET Framework 4.6.2, o descriptografador <xref:System.Security.Cryptography.AesCryptoServiceProvider> fornece uma transformação reutilizável. Após uma chamada para <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=name>, a transformação é reinicializada e pode ser reutilizada. Para aplicativos destinados a versões anteriores do .NET Framework, tentar reutilizar o descriptografador chamando <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=name> após uma chamada para <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=name> gera um <xref:System.Security.Cryptography.CryptographicException> ou produz dados corrompidos.|
|Sugestão|O impacto dessa alteração deve ser mínimo, uma vez que se trata do comportamento esperado. Aplicativos que dependem do comportamento anterior podem optar por não usá-lo adicionando a seguinte definição de configuração à seção <code>&lt;runtime&gt;</code> do arquivo de configuração do aplicativo:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Além disso, aplicativos destinados a uma versão anterior do .NET Framework, mas em execução em uma versão do .NET Framework a partir do .NET Framework 4.6.2 podem aceitá-lo adicionando a seguinte definição de configuração à seção <code>&lt;runtime&gt;</code> do arquivo de configuração do aplicativo:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Escopo|Secundária|
|Versão|4.6.2|
|Type|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor?displayProperty=nameWithType></li></ul>|
