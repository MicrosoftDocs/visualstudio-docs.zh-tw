---
title: "IDebugProperty2::GetParent | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::GetParent"
helpviewer_keywords: 
  - "IDebugProperty2::GetParent"
ms.assetid: 58780469-fe25-4d84-9187-67940ca0767f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProperty2::GetParent
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得屬性的父代屬性。  
  
## 語法  
  
```cpp#  
HRESULT GetParent (   
   IDebugProperty2** ppParent  
);  
```  
  
```c#  
int GetParent (   
   out IDebugProperty2 ppParent  
);  
```  
  
#### 參數  
 `ppParent`  
 \[\] out傳回[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) ，表示屬性的父物件。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則會傳回錯誤碼。  傳回`S_GETPARENT_NO_PARENT`如果沒有父代。  
  
## 請參閱  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)