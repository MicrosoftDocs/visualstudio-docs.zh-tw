---
title: "IEEVisualizerDataProvider::SetObjectForVisualizer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerDataProvider::SetObjectForVisualizer"
helpviewer_keywords: 
  - "IEEVisualizerDataProvider::SetObjectForVisualizer 方法"
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEEVisualizerDataProvider::SetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會變更物件，表示視覺化檢視。  
  
## 語法  
  
```cpp  
HRESULT SetObjectForVisualizer(  
   IDebugObject*  pNewObject,  
   BSTR*          error,  
   IDebugObject** pException  
);  
```  
  
```c#  
int SetObjectForVisualizer(  
   IDebugObject     pNewObject,  
   out string       error,  
   out IDebugObject pException  
);  
```  
  
#### 參數  
 `pNewObject`  
 \[in\]要設定的物件。  
  
 `error`  
 \[\] out如果設定物件時發生錯誤，這個字串會保留的錯誤訊息。  
  
 `pException`  
 \[\] out如果有錯誤發生，此物件會保留例外狀況資訊。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 它是由實作器來判斷錯誤資訊之傳回方式。  不過，很可能有些呼叫端可能只以查看是否有知道，已傳回例外狀況物件的外觀時，發生錯誤，所以如果發生錯誤，這個方法永遠會傳回例外狀況物件。  錯誤字串應該要提供模糊的呼叫端想要讓它的使用。  
  
## 請參閱  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)