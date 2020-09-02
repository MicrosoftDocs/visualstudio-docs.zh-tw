---
title: PENDING_BP_STATE_INFO |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE_INFO
helpviewer_keywords:
- PENDING_BP_STATE_INFO structure
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: af22ef2d8a77b8c44b9e494736630480a0614162
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205063"
---
# <a name="pending_bp_state_info"></a>PENDING_BP_STATE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

包含已準備系結至程式碼位置之中斷點狀態的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
typedef struct _tagPENDING_BP_STATE_INFO {   
   PENDING_BP_STATE       state;  
   PENDING_BP_STATE_FLAGS flags;  
} PENDING_BP_STATE_INFO;  
```  
  
```csharp  
public struct PENDING_BP_STATE_INFO {   
   public uint state;  
   public uint flags;  
};  
```  
  
## <a name="members"></a>成員  
 state  
 [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)列舉中的值，這個值會指定暫止中斷點的狀態。  
  
 flags  
 [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)列舉中的旗標組合，指定中斷點是否虛擬化。  
  
## <a name="remarks"></a>備註  
 此結構會傳遞至其填入的 [>getstate](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md) 方法。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [>getstate](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)   
 [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)   
 [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)
