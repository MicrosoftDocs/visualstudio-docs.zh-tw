---
title: "IDebugProcess2::CanDetach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::CanDetach"
helpviewer_keywords: 
  - "IDebugProcess2::CanDetach"
ms.assetid: 2830f7c3-69fb-474a-97b8-5b869e38d546
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::CanDetach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

判斷工作階段偵錯管理員 \(SDM\) 可以中斷連結處理序。  
  
## 語法  
  
```cpp#  
HRESULT CanDetach(  
   void  
);  
```  
  
```c#  
int CanDetach();  
```  
  
## 傳回值  
 如果成功的話，會傳回`S_OK.`會傳回`S_FALSE`如果偵錯工具無法從處理序中斷連結。  否則，會傳回錯誤碼。  
  
## 請參閱  
 [CanDetach](../Topic/IDebugProgram2::CanDetach.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)