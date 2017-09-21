---
title: "IEEVisualizerDataProvider::GetObjectForVisualizer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerDataProvider::GetObjectForVisualizer"
helpviewer_keywords: 
  - "IEEVisualizerDataProvider::GetObjectForVisualizer 方法"
ms.assetid: bd5376fc-13b4-40b7-9a5d-7ba8289f1b24
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IEEVisualizerDataProvider::GetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會取得物件，表示這個視覺化檢視。  
  
## 語法  
  
```cpp  
HRESULT GetObjectForVisualizer(  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int GetObjectForVisualizer(  
   out IDebugObject ppObject  
);  
```  
  
#### 參數  
 `ppObject`  
 \[\] out代表這個視覺化檢視物件  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 `GetObjectForVisualizer`可傳回物件的快取的版本。  如果在呼叫端想要確定物件是最新狀態，然後它會呼叫[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)。  
  
## 請參閱  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)