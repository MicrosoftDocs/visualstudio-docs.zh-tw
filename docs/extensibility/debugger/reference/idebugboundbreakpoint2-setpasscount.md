---
title: IDebugBoundBreakpoint2::SetPassCount |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBoundBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugBoundBreakpoint2::SetPassCount method
ms.assetid: b32c12f9-b34d-43bd-a1b9-61af6cf8e51b
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 77a604f10029aa94dd1632aa656c3e7a2827e823
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugboundbreakpoint2setpasscount"></a>IDebugBoundBreakpoint2::SetPassCount
設定或變更與此繫結中斷點相關聯的密碼計數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
```csharp  
int SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
#### <a name="parameters"></a>參數  
 `bpPassCount`  
 [in][BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)結構，指定傳遞計數。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。 傳回`E_BP_DELETED`如果繫結的中斷點物件的狀態設定為`BPS_DELETED`(屬於[BP_STATE](../../../extensibility/debugger/reference/bp-state.md)列舉型別)。  
  
## <a name="remarks"></a>備註  
 通過計數決定當引發中斷點。 藉由呼叫，則可以取得目前行程或叫用的次數[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)方法。  
  
 與此中斷點先前關聯任何傳遞計數將會遺失。  
  
## <a name="see-also"></a>請參閱  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)