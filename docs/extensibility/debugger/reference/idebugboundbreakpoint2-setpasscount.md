---
title: "IDebugBoundBreakpoint2::SetPassCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBoundBreakpoint2::SetPassCount"
helpviewer_keywords: 
  - "SetPassCount 方法"
  - "IDebugBoundBreakpoint2::SetPassCount 方法"
ms.assetid: b32c12f9-b34d-43bd-a1b9-61af6cf8e51b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugBoundBreakpoint2::SetPassCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

設定或變更此繫結中斷點相關聯的行程計數。  
  
## 語法  
  
```cpp#  
HRESULT SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
```c#  
int SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
#### 參數  
 `bpPassCount`  
 \[in\][BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)指定行程計數的結構。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  傳回`E_BP_DELETED`如果繫結的中斷點物件的狀態會設定為`BPS_DELETED` \(屬於[BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)列舉型別\)。  
  
## 備註  
 通過計數會決定中斷點時引發。  目前的階段或叫用的次數可由呼叫[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)方法。  
  
 任何先前關聯此中斷點的行程計數將會遺失。  
  
## 請參閱  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)