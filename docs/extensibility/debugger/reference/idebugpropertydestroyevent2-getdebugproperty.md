---
title: "IDebugPropertyDestroyEvent2::GetDebugProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPropertyDestroyEvent2::GetDebugProperty"
helpviewer_keywords: 
  - "IDebugPropertyDestroyEvent2::GetDebugProperty"
ms.assetid: c96ae785-0ac8-4df4-8df3-15a8d7e13687
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPropertyDestroyEvent2::GetDebugProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得要終結的屬性。  
  
## 語法  
  
```cpp#  
HRESULT GetDebugProperty (   
   IDebugProperty2** ppProperty  
);  
```  
  
```c#  
int GetDebugProperty (   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### 參數  
 `ppProperty`  
 \[\] out傳回[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)物件，表示要終結的屬性。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)