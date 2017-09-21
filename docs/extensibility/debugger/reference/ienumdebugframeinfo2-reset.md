---
title: "IEnumDebugFrameInfo2::Reset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugFrameInfo2::Reset"
helpviewer_keywords: 
  - "IEnumDebugFrameInfo2::Reset"
ms.assetid: e149b559-f072-480b-9552-a452b147f3a8
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugFrameInfo2::Reset
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

將重設第一個項目，為列舉型別。  
  
## 語法  
  
```cpp#  
HRESULT Reset(  
   void  
);  
```  
  
```c#  
int Reset();  
```  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 這個方法呼叫下, 一步呼叫之後[下一步](../Topic/IEnumDebugFrameInfo2::Next.md)方法會傳回列舉型別的第一個項目。  
  
## 請參閱  
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)