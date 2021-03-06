---
title: Authenticode (referência de API não gerenciada)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
ms.openlocfilehash: 1b8b2222950c75f7f9d2ec2704f722087645cd7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73132463"
---
# <a name="authenticode-unmanaged-api-reference"></a>Authenticode (referência de API não gerenciada)
Oferece suporte à criação de licença Authenticode XrML e módulo de verificação.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Função _AxlGetIssuerPublicKeyHash](axlgetissuerpublickeyhash-function.md)  
 Recupera o hash SHA-1 da chave pública associada à chave privada usada para assinar o certificado especificado.  
  
 [Função _AxlPublicKeyBlobToPublicKeyToken](axlpublickeyblobtopublickeytoken-function.md)  
 Computa o token de chave pública do nome forte de um formato CSP PUBLICKEYBLOB.  
  
 [Função _AxlRSAKeyValueToPublicKeyToken](axlrsakeyvaluetopublickeytoken-function.md)  
 Converte um Módulo e um Expoente em um token de chave pública com nome forte.  
  
 [Função CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md)  
 Libera os recursos alocados para a estrutura AXL_AUTHENTICODE_SIGNER_INFO.  
  
 [Função CertFreeAuthenticodeTimestamperInfo](certfreeauthenticodetimestamperinfo-function.md)  
 Libera recursos alocados para a estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO.  
  
 [Função CertTimestampAuthenticodeLicense](certtimestampauthenticodelicense-function.md)  
 Adiciona carimbo de data/hora a uma licença Authenticode XrML criada por CertCreateAuthenticodeLicense.  
  
 [Função CertVerifyAuthenticodeLicense](certverifyauthenticodelicense-function.md)  
 Verifica a validade de uma licença XrML Authenticode.  
  
 [Estrutura AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md)  
 Define as informações sobre o signatário do Authenticode.  
  
 [Estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md)  
 Define as informações sobre o carimbo de data/hora do Authenticode.  
  
## <a name="see-also"></a>Confira também

- [Referência de API não gerenciada](../index.md)
