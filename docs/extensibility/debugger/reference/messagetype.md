---
title: "訊息類型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MESSAGETYPE"
helpviewer_keywords: 
  - "訊息類型列舉"
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 訊息類型
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定的訊息類型和原因。  
  
## 語法  
  
```cpp#  
enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
typedef DWORD MESSAGETYPE;  
```  
  
```c#  
public enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
```  
  
## Members  
 MT\_OUTPUTSTRING  
 表示應該傳送郵件，在 \[輸出\] 視窗。  這是互斥的`MT_MESSAGEBOX`。  
  
 MT\_MESSAGEBOX  
 指出訊息應該會顯示在訊息方塊。  這是互斥的`MT_OUTPUTSTRING`。  
  
 MT\_TYPE\_MASK  
 若要找出郵件的目的地遮罩值。  
  
 MT\_REASON\_EXCEPTION  
 表示正在將訊息方塊顯示例外狀況的結果。  這是互斥的`MT_REASON_TRACEPOINT`。  
  
 MT\_REASON\_TRACEPOINT  
 表示正在將訊息方塊顯示的方式來點擊追蹤點。  這是互斥`MT_REASON_EXCEPTION`。  
  
 MT\_REASON\_MASK  
 遮罩值，以找出目前未顯示的訊息的原因。  
  
## 備註  
 這些值會傳回從[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)和[GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)方法。  
  
 其中一個原因值可以與其中使用位元的輸出目的地值結合`OR`。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)