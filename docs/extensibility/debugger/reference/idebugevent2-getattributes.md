---
title: "IDebugEvent2::GetAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEvent2::GetAttributes"
helpviewer_keywords: 
  - "IDebugEvent2::GetAttributes"
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEvent2::GetAttributes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得此偵錯事件的屬性。  
  
## 語法  
  
```cpp#  
HRESULT GetAttribute(   
   DWORD* pdwAttrib  
);  
```  
  
```c#  
int GetAttribute(   
   out uint pdwAttrib  
);  
```  
  
#### 參數  
 `pdwAttrib`  
 \[\] out從的旗標組合[EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)列舉型別。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面是通用於所有的事件。  這個方法將告訴您事件 ； 的型別 比方說，是同步或非同步的事件，又會停止事件。  
  
## 請參閱  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)