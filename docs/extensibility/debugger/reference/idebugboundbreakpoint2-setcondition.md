---
title: "IDebugBoundBreakpoint2::SetCondition | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBoundBreakpoint2::SetCondition"
helpviewer_keywords: 
  - "SetCondition 方法"
  - "IDebugBoundBreakpoint2::SetCondition 方法"
ms.assetid: 5d366876-efed-43d0-8ea1-dfdb009cbfac
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugBoundBreakpoint2::SetCondition
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

設定或變更此繫結中斷點相關聯的條件。  
  
## 語法  
  
```cpp#  
HRESULT SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
```c#  
int SetCondition(   
   enum_BP_CONDITION bpCondition  
);  
```  
  
#### 參數  
 `bpCondition`  
 \[in\]介於[BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)列舉型別描述項狀態。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  傳回`E_BP_DELETED`如果繫結的中斷點物件的狀態會設定為`BPS_DELETED` \(屬於[BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)列舉型別\)。  
  
## 備註  
 任何先前關聯此中斷點的條件將會遺失。  
  
## 請參閱  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)