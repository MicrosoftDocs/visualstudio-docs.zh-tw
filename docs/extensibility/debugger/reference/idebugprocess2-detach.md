---
title: "IDebugProcess2::Detach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::Detach"
helpviewer_keywords: 
  - "IDebugProcess2::Detach"
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::Detach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

中斷此處理程序與偵錯工具中斷連結所有的程式處理序中的連結。  
  
## 語法  
  
```cpp#  
HRESULT Detach(   
   void   
);  
```  
  
```c#  
int Detach();  
```  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 所有程式，以及程序繼續執行，但無法再偵錯工作階段的一部份。  卸離作業後就會傳送事件，此程序 \(和它的程式\) 的完整且沒有其他偵錯。  
  
## 請參閱  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)