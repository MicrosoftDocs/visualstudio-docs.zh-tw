---
title: "IPropertyProxyProvider::GetPropertyProxy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IPropertyProxyProvider::GetPropertyProxy"
helpviewer_keywords: 
  - "IPropertyProxyProvider::GetPropertyProxy"
ms.assetid: 3ebb7515-5bfe-48f4-9b8d-721b8f664eb6
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IPropertyProxyProvider::GetPropertyProxy
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取屬性的 proxy 介面指定的 proxy 的 id。  
  
## 語法  
  
```cpp#  
HRESULT GetPropertyProxy(  
   DWORD                  dwID,  
   IPropertyProxyEESide** proxy  
);  
```  
  
```c#  
int GetPropertyProxy(  
   uint                     dwID,  
   out IPropertyProxyEESide proxy  
);  
```  
  
#### 參數  
 `dwID`  
 \[in\]您想要的屬性 proxy 的 ID。  
  
 `proxy`  
 \[\] out傳回[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)物件。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 若要支援外部型別視覺化檢視，這個方法通常傳送呼叫至[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)方法。  請參閱[視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)如 IEEVisualizerService 的取得方式的詳細資訊。  
  
## 請參閱  
 [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)