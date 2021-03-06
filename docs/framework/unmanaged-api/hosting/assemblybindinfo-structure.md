---
title: Estrutura AssemblyBindInfo
ms.date: 03/30/2017
api_name:
- AssemblyBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyBindInfo
helpviewer_keywords:
- AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type:
- apiref
ms.openlocfilehash: 8764a3d665c997460419561eb168f92ca769c30c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192107"
---
# <a name="assemblybindinfo-structure"></a>Estrutura AssemblyBindInfo
Fornece informações detalhadas sobre o assembly referenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`dwAppDomainId`|Um identificador exclusivo para o `IStream` retornado por uma chamada para [IHostAssemblyStore::P rovideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), da qual o assembly referenciado deve ser carregado.|  
|`lpReferencedIdentity`|Um identificador exclusivo para o assembly referenciado.|  
|`lpPostPolicyIdentity`|O identificador para o assembly referenciado após a aplicação de qualquer valor de política de associação.|  
|`ePolicyLevel`|Um dos valores de [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) que indicam quais políticas de controle de versão, se houver, deve ser aplicado ao assembly referenciado.|  
  
## <a name="remarks"></a>Comentários  
 O host fornece o identificador exclusivo `dwAppDomainId` para o Common Language Runtime (CLR). Após uma chamada para `IHostAssemblyStore::ProvideAssembly` retorna, o tempo de execução usa o identificador para determinar se o conteúdo do `IStream` foi mapeado. Nesse caso, o tempo de execução carrega a cópia existente em vez de remapear o fluxo. O tempo de execução também usa esse identificador como uma chave de pesquisa para fluxos retornados de chamadas para [IHostAssemblyStore::P rovidemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md). Portanto, o identificador deve ser exclusivo para solicitações de módulo e para solicitações de assembly.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. idl  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [Interface ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [Interface ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [Interface IHostAssemblyManager](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [Interface IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [Estrutura ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)
