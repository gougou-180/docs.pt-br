---
title: Método ICorDebugStackWalk::GetContext
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetContext
helpviewer_keywords:
- GetContext method, ICorDebugStackWalk interface [.NET Framework debugging]
- ICorDebugStackWalk::GetContext method [.NET Framework debugging]
ms.assetid: 081d1c95-152b-4797-8552-18453eb7b14b
topic_type:
- apiref
ms.openlocfilehash: 9953d0f3e1a4d4cd935918f0e5721e474453ca7d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791903"
---
# <a name="icordebugstackwalkgetcontext-method"></a>Método ICorDebugStackWalk::GetContext
Retorna o contexto para o quadro atual no objeto [ICorDebugStackWalk](icordebugstackwalk-interface.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `contextFlags`  
 no Sinalizadores que indicam o conteúdo solicitado do buffer de contexto (definido em WinNT. h).  
  
 `contextBufSize`  
 no O tamanho alocado do buffer de contexto.  
  
 `contextSize`  
 fora O tamanho real do contexto. Esse valor deve ser menor ou igual ao tamanho do buffer de contexto.  
  
 `contextBuf`  
 fora O buffer de contexto.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O contexto do quadro atual foi retornado com êxito.|  
|{1&gt;E_FAIL&lt;1}|Não foi possível retornar o contexto.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)|O buffer de contexto é muito pequeno.|  
|CORDBG_E_PAST_END_OF_STACK|O ponteiro de quadro já está no final da pilha; Portanto, nenhum quadro adicional pode ser acessado.|  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
 Como o desenrolamento restaura apenas um subconjunto dos registros, como registros não-voláteis, o contexto pode não corresponder exatamente ao estado de registro no momento da chamada.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
