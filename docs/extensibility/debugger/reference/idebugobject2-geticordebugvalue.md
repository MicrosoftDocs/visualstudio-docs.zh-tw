---
title: "IDebugObject2::GetICorDebugValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2::GetICorDebugValue"
helpviewer_keywords: 
  - "IDebugObject2::GetICorDebugValue 方法"
ms.assetid: bcd4355d-3fbe-483f-bb23-a44348323c6a
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugObject2::GetICorDebugValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得受管理的程式碼物件，表示這個物件相關聯的值。  
  
## 語法  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```c#  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### 參數  
 `ppUnk`  
 \[\] out`IUnknown` ，表示這個別名的介面。  這個介面可以查詢`ICorDebugValue`介面。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
## 備註  
 `ICorDebugValue`物件是一種 Common Language Runtime 介面，代表的值。  
  
## 請參閱  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)