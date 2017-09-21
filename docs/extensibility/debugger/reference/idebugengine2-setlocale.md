---
title: "IDebugEngine2::SetLocale | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::SetLocale"
helpviewer_keywords: 
  - "IDebugEngine2::SetLocale"
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngine2::SetLocale
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

設定偵錯引擎 \(DE\) 的地區設定。  
  
## 語法  
  
```cpp#  
HRESULT SetLocale(   
   WORD wLangID  
);  
```  
  
```c#  
int SetLocale(   
   ushort wLangID  
);  
```  
  
#### 參數  
 `wLangID`  
 \[in\]指定語言的地區設定。  例如，英文的 1033。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 工作階段偵錯管理員 \(SDM\) 傳播 IDE 的地區設定，以便 DE 所傳回的字串已正確地當地語系化會呼叫這個方法。  
  
## 請參閱  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)