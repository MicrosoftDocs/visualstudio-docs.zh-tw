---
title: "BP_CONDITION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_CONDITION"
helpviewer_keywords: 
  - "BP_CONDITION 結構"
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_CONDITION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

描述在其下觸發中斷點的條件。  
  
## 語法  
  
```cpp#  
typedef struct _BP_CONDITION {   
   IDebugThread2* pThread;  
   BP_COND_STYLE  styleCondition;  
   BSTR           bstrContext;  
   BSTR           bstrCondition;  
   UINT           nRadix;  
} BP_CONDITION;  
```  
  
```c#  
public struct BP_CONDITION {   
   public IDebugThread2 pThread;  
   public uint          styleCondition;  
   public string        bstrContext;  
   public string        bstrCondition;  
   public uint          nRadix;  
};  
```  
  
## Members  
 `pThread`  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件，代表使用中的執行緒，包含中斷點的應用程式。  
  
 `styleCondition`  
 介於[BP\_COND\_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)列舉型別描述此中斷點條件的樣式。  
  
 `bstrContext`  
 中斷點的位置。  
  
 `bstrCondition`  
 引發之中斷點的條件。  
  
 `nRadix`  
 若要用來評估任何數字資訊的基數。  
  
## 備註  
 這個結構屬於[BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)和[BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)結構。  
  
 此結構也會當做參數傳遞[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)和[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)方法。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)   
 [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP\_COND\_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)