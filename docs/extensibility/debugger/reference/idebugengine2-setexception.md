---
title: "IDebugEngine2::SetException | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::SetException"
helpviewer_keywords: 
  - "IDebugEngine2::SetException"
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngine2::SetException
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定偵錯引擎 \(DE\) 應如何處理指定的例外狀況。  
  
## 語法  
  
```cpp#  
HRESULT SetException(   
   EXCEPTION_INFO* pException  
);  
```  
  
```c#  
int SetException(   
   EXCEPTION_INFO[] pException  
);  
```  
  
#### 參數  
 `pException`  
 \[in\][EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)結構描述例外狀況，以及如何進行偵錯。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 若要停止產生在初次出現例外狀況的程式、 秒的機率，可指示將 DE 或根本不。  
  
## 請參閱  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)