---
title: "IDebugEnumField::GetStringFromValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEnumField::GetStringFromValue"
helpviewer_keywords: 
  - "IDebugEnumField::GetStringFromValue 方法"
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugEnumField::GetStringFromValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會取得指定其值的列舉常數的名稱。  
  
## 語法  
  
```cpp#  
HRESULT GetStringFromValue(  
   ULONGLONG value,  
   BSTR*     pbstrValue  
);  
```  
  
```c#  
int GetStringFromValue(  
   ulong      value,  
   out string pbstrValue  
);  
```  
  
#### 參數  
 `value`  
 \[in\]要取得的列舉型別名稱的常值。  
  
 `pbstrValue`  
 \[\] out傳回列舉型別常數的名稱。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`如果沒有相關聯的名稱，或傳回錯誤碼的值。  
  
## 備註  
 如果有多個相同的值相關聯的名稱，將會傳回列舉型別中定義的名字。  
  
## 請參閱  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)