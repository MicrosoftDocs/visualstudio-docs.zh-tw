---
title: "IDebugProperty2::GetDerivedMostProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::GetDerivedMostProperty"
helpviewer_keywords: 
  - "IDebugProperty2::GetDerivedMostProperty"
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProperty2::GetDerivedMostProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得屬性的衍生最徹底的屬性。  
  
## 語法  
  
```cpp#  
HRESULT GetDerivedMostProperty (   
   IDebugProperty2** ppDerivedMost  
);  
```  
  
```c#  
int GetDerivedMostProperty (   
   out IDebugProperty2 ppDerivedMost  
);  
```  
  
#### 參數  
 `ppDerivedMost`  
 \[\] out傳回[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)物件，表示衍生最徹底的屬性。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則會傳回錯誤碼。  傳回`S_GETDERIVEDMOST_NO_DERIVED_MOST`如果沒有衍生最徹底的屬性來擷取。  
  
## 備註  
 比方說，如果這個屬性描述物件實作`ClassRoot`也就是實際的執行個體化，但`ClassDerived` ，衍生自`ClassRoot`，那麼這個方法會傳回[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)物件描述`ClassDerived`物件。  
  
## 請參閱  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)