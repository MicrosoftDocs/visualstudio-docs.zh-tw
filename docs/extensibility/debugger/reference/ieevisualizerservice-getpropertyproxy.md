---
title: "IEEVisualizerService::GetPropertyProxy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerService::GetPropertyProxy"
helpviewer_keywords: 
  - "IEEVisualizerService::GetPropertyProxy 方法"
ms.assetid: 748750f4-76e7-4580-9da2-afba07681b37
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEEVisualizerService::GetPropertyProxy
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會傳回屬性的物件的 proxy。  
  
## 語法  
  
```cpp  
HRESULT GetPropertyProxy(  
   DWORD                  dwID,  
   IPropertyProxyEESide** proxy  
);  
```  
  
```c#  
int GetPropertyProxy(  
   uint                     dwID,  
   out IPropertyProxyEESide proxy  
);  
```  
  
#### 參數  
 `dwID`  
 \[in\]若要擷取的屬性 proxy 的 ID。  
  
 `proxy`  
 \[\] out需要 proxy 中實作[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)介面。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)型別視覺化檢視，將要求傳遞至這個方法做為其支援的一部分。  
  
## 請參閱  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)