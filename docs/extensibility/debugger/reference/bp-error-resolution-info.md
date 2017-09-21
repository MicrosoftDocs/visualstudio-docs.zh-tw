---
title: "BP_ERROR_RESOLUTION_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_ERROR_RESOLUTION_INFO"
helpviewer_keywords: 
  - "BP_ERROR_RESOLUTION_INFO 結構"
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# BP_ERROR_RESOLUTION_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

描述錯誤的中斷點，包括位置、 程式及執行緒的解析度。  
  
## 語法  
  
```cpp#  
typedef struct _BP_ERROR_RESOLUTION_INFO {   
   BPERESI_FIELDS         dwFields;  
   BP_RESOLUTION_LOCATION bpResLocation;  
   IDebugProgram2*        pProgram;  
   IDebugThread2*         pThread;  
   BSTR                   bstrMessage;  
   BP_ERROR_TYPE          dwType;  
} BP_ERROR_RESOLUTION_INFO;  
```  
  
```c#  
public struct BP_ERROR_RESOLUTION_INFO {   
   public uint                   dwFields;  
   public BP_RESOLUTION_LOCATION bpResLocation;  
   public IDebugProgram2         pProgram;  
   public IDebugThread2          pThread;  
   public string                 bstrMessage;  
   public uint                   dwType;  
};  
```  
  
## Members  
 `dwFields`  
 從值的組合[BPERESI\_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md)指定的欄位，此結構會填寫列舉型別。  
  
 `bpResLocation`  
 [BP\_RESOLUTION\_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)等位，指定中斷點的解析度位置。  
  
 `pProgram`  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件，代表中斷點錯誤發生的應用程式。  
  
 `pThread`  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件，表示產生中斷點錯誤的應用程式正在執行的執行緒。  
  
 `bstrMessage`  
 字串，包含造成這個錯誤解析的任何警告或錯誤訊息。  
  
 `dwType`  
 介於[BP\_ERROR\_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)指定中斷點的錯誤類型的列舉型別。  
  
## 備註  
 這個結構會傳回從[GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)方法。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)   
 [BPRESI\_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)   
 [BP\_RESOLUTION\_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP\_ERROR\_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)