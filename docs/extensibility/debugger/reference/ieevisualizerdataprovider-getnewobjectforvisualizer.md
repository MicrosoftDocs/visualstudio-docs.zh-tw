---
title: "IEEVisualizerDataProvider::GetNewObjectForVisualizer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerDataProvider::GetNewObjectForVisualizer"
helpviewer_keywords: 
  - "IEEVisualizerDataProvider::GetNewObjectForVisualizer 方法"
ms.assetid: a898d549-4898-4fde-aad1-e8bb89129652
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEEVisualizerDataProvider::GetNewObjectForVisualizer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會取得新的物件的視覺化檢視。  這個方法永遠會建立一個新的物件，從現有的物件。  
  
## 語法  
  
```cpp  
HRESULT GetNewObjectForVisualizer(  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int GetNewObjectForVisualizer(  
   out IDebugObject ppObject  
);  
```  
  
#### 參數  
 `ppObject`  
 \[\] out新的物件。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 `This method`對其重新評估目前是表示，並傳回結果做為新物件的物件。  評估的結果，將會更新現有的物件。  
  
## 請參閱  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)