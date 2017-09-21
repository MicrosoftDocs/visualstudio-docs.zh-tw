---
title: "IDebugField::GetInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::GetInfo"
helpviewer_keywords: 
  - "IDebugField::GetInfo 方法"
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugField::GetInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會取得的欄位可顯示的資訊。  
  
## 語法  
  
```cpp#  
HRESULT GetInfo(   
   FIELD_INFO_FIELDS dwFields,  
   FIELD_INFO* pFieldInfo  
);  
```  
  
```c#  
int GetInfo(  
   enum_FIELD_INFO_FIELDS dwFields,  
   FIELD_INFO[] pFieldInfo  
);  
```  
  
#### 參數  
 `dwFields`  
 \[in\]結合[FIELD\_INFO\_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)的常數，選取要顯示的資訊。  如果欄位是代表一個符號，這通常是符號名稱和型別。  
  
 `pFieldInfo`  
 \[\] out傳回的資訊提供的[FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)結構。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)