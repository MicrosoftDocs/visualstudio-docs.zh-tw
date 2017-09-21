---
title: "BP_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_FLAGS"
helpviewer_keywords: 
  - "BP_FLAGS 列舉型別"
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

提供可以用來設定中斷點時指定的其他資訊的選擇性旗標。  
  
## 語法  
  
```cpp#  
enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
typedef DWORD BP_FLAGS;  
```  
  
```c#  
public enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
```  
  
## Members  
 BP\_FLAG\_NONE  
 指定沒有中斷點旗標。  
  
 BP\_FLAG\_MAP\_DOCPOSITION  
 指定偵錯引擎 \(DE\) 應該會將對應使用的文件位置的中斷點。  這是僅適用於如動態伺服器網頁 \(ASP\) 的指令碼導向的原始程式檔中設定中斷點。  
  
 BP\_FLAG\_DONT\_STOP  
 指定中斷點應該由偵錯引擎，但偵錯引擎最後應該停止那里 \(也就是[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)不會傳送事件的物件\)。  這個旗標被為了主要是用於追蹤點。  
  
## 備註  
 用於`dwFlags`成員的[BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)和[BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)結構。  
  
 這些值可以使用位元和結合`OR`。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)