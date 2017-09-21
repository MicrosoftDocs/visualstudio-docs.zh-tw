---
title: "IDebugField::GetTypeInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::GetTypeInfo"
helpviewer_keywords: 
  - "IDebugField::GetTypeInfo 方法"
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugField::GetTypeInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會取得型別無關的符號或型別資訊。  
  
## 語法  
  
```cpp#  
HRESULT GetTypeInfo(   
   TYPE_INFO* pTypeInfo  
);  
```  
  
```c#  
int GetTypeInfo(  
   TYPE_INFO[] pTypeInfo  
);  
```  
  
#### 參數  
 `pTypeInfo`  
 \[\] out傳回提供的輸入資訊[TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)結構。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 例如，型別無關的資訊應包含 AppDomain、 模組和類別，其中包含該符號。  
  
## 請參閱  
 [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)