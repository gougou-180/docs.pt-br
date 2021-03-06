---
title: Método ICorDebugProcess5::GetTypeLayout
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeLayout
helpviewer_keywords:
- ICorDebugProcess5::GetTypeLayout method [.NET Framework debugging]
- GetTypeLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: bd62f5d1-e874-41f1-81e5-a29a7572c15d
topic_type:
- apiref
ms.openlocfilehash: 306d881c05c2fcdb15a53a439bfce6eff3afffa8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792307"
---
# <a name="icordebugprocess5gettypelayout-method"></a>Método ICorDebugProcess5::GetTypeLayout
Obtém informações sobre o layout de um objeto na memória com base em seu identificador de tipo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `id`  
 no Um [COR_TYPEID](cor-typeid-structure.md) token que especifica o tipo cujo layout é desejado.  
  
 `pLayout`  
 fora Um ponteiro para uma estrutura de [COR_TYPE_LAYOUT](cor-type-layout-structure.md) que contém informações sobre o layout do objeto na memória.  
  
## <a name="remarks"></a>Comentários  
 O método `ICorDebugProcess5::GetTypeLayout` fornece informações sobre um objeto com base em seu [COR_TYPEID](cor-typeid-structure.md), que é retornado por vários outros métodos [ICorDebugProcess5](icordebugprocess5-interface.md) . As informações são fornecidas por uma estrutura de [COR_TYPE_LAYOUT](cor-type-layout-structure.md) que é populada pelo método.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Estrutura COR_TYPE_LAYOUT](cor-type-layout-structure.md)
- [Interface ICorDebugProcess5](icordebugprocess5-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
