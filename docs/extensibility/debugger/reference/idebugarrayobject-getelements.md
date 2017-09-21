---
title: "IDebugArrayObject::GetElements | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayObject::GetElements"
helpviewer_keywords: 
  - "IDebugArrayObject::GetElements 方法"
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugArrayObject::GetElements
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得陣列的所有項目的列舉值。  
  
## 語法  
  
```cpp#  
HRESULT GetElements(   
   IEnumDebugObjects** ppEnum  
);  
```  
  
```c#  
int GetElements(  
   out IEnumDebugObjects ppEnum  
);  
```  
  
#### 參數  
 `ppEnum`  
 \[\] out傳回[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)可讓所有的項目上列舉的物件。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
## 備註  
 或者，使用[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)和[GetElement](../Topic/IDebugArrayObject::GetElement.md)方法來逐一查看的項目。  
  
## 請參閱  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)