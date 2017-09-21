---
title: "IDebugArrayField::GetNumberOfElements | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayField::GetNumberOfElements"
helpviewer_keywords: 
  - "IDebugArrayField::GetNumberOfElements 方法"
ms.assetid: a1961ef3-d69d-4022-b8c9-b9cfb9811345
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugArrayField::GetNumberOfElements
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得陣列中的項目數。  
  
## 語法  
  
```cpp#  
HRESULT GetNumberOfElements(   
   DWORD* pdwNumElements  
);  
```  
  
```c#  
int GetNumberOfElements(  
   out uint pdwNumElements  
);  
```  
  
#### 參數  
 `pdwNumElements`  
 \[\] out傳回陣列中的項目數。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
## 備註  
 傳回的值是在陣列中，不論維度數目的元素總數。  
  
## 請參閱  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)