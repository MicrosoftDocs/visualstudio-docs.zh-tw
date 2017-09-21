---
title: "BP_REQUEST_INFO2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_REQUEST_INFO2"
helpviewer_keywords: 
  - "BP_REQUEST_INFO2 結構"
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# BP_REQUEST_INFO2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

包含實作 \[中斷點\] 後，其中包括廠商的 GUID、 條件約束和追蹤點所需的資訊。  
  
## 語法  
  
```cpp#  
typedef struct _BP_REQUEST_INFO2 {  
   BPREQI_FIELDS   dwFields;  
   GUID            guidLanguage;  
   BP_LOCATION     bpLocation;  
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   IDebugThread2*  pThread;  
   BSTR            bstrThreadName;  
   BP_CONDITION    bpCondition;  
   BP_PASSCOUNT    bpPassCount;  
   BP_FLAGS        dwFlags;  
   GUID            guidVendor;  
   BSTR            bstrConstraint;  
   BSTR            bstrTracepoint;  
} BP_REQUEST_INFO2;  
```  
  
```c#  
public struct BP_REQUEST_INFO2 {  
   public uint           dwFields;  
   public Guid           guidLanguage;  
   public BP_LOCATION    bpLocation;  
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public IDebugThread2  pThread;  
   public string         bstrThreadName;  
   public BP_CONDITION   bpCondition;  
   public BP_PASSCOUNT   bpPassCount;  
   public uint           dwFlags;  
   public Guid           guidVendor;  
   public string         bstrConstraint;  
   public string         bstrTracepoint;  
};  
```  
  
## Members  
 `dwFields`  
 從的旗標組合[BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)指定哪些欄位已填寫的列舉型別。  
  
 `guidLanguage`  
 語言的 GUID。  
  
 `bpLocation`  
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)指定的中斷點位置類型的結構。  
  
 `pProgram`  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件，代表中斷點發生於應用程式。  
  
 `bstrProgramName`  
 中斷點會發生在應用程式的名稱。  
  
 `pThread`  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)表示中斷點會發生執行緒的物件。  
  
 `bstrThreadName`  
 中斷點會發生的執行緒的名稱。  
  
 `bpCondition`  
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)結構描述在其下會引發的中斷點的條件。  
  
 `bpPassCount`  
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)結構，包含中斷點的行程計數資訊。  
  
 `dwFlags`  
 從的旗標組合[BP\_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) ，指定所要求的中斷點的旗標列舉型別。  
  
 `guidVendor`  
 廠商的 GUID。  可能是 null 值。  
  
 `bstrConstraint`  
 中斷點條件約束的名稱。  可能是 null 值。  
  
 `bstrTracepoint`  
 追蹤點的名稱。  可能是 null 值。  
  
## 備註  
 傳回此結構[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)方法。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)   
 [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP\_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)