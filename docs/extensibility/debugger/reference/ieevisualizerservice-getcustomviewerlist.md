---
title: "IEEVisualizerService::GetCustomViewerList | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerService::GetCustomViewerList"
helpviewer_keywords: 
  - "IEEVisualizerService::GetCustomViewerList 方法"
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEEVisualizerService::GetCustomViewerList
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會傳回這項服務所知的型別視覺化檢視的清單。  
  
## 語法  
  
```cpp  
HRESULT GetCustomViewerList(  
   ULONG                celtSkip,  
   ULONG                celtRequested,  
   DEBUG_CUSTOM_VIEWER* rgViewers,  
   ULONG*               pceltFetched  
);  
```  
  
```c#  
int GetCustomViewerList(  
   uint                  celtSkip,  
   uint                  celtRequested,  
   DEBUG_CUSTOM_VIEWER[] rgViewers,  
   out uint              pceltFetched  
);  
```  
  
#### 參數  
 `celtSkip`  
 \[in\]略過的視覺化檢視的數目。  
  
 `celRequested`  
 \[in\]若要擷取的視覺化檢視的數目 \(也會指定大小的`rgViewers`陣列\)。  
  
 `rgViewers`  
 輸入 \[、 輸出\]陣列的[DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)結構，以填入。  
  
 `pceltFetched`  
 \[\] out實際擷取的視覺化檢視的數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)型別視覺化檢視，將要求傳遞至這個方法做為其支援的一部分。  如果運算式評估工具也會提供相同類型的自訂檢視器，可以將附加適當填寫[DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)這些自訂的檢視器清單的結構。  請確定[GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md)會反映這些額外的檢視器。  
  
 請參閱[類型的視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)如需詳細資訊，在視覺化檢視和檢視器之間的差異。  
  
## 請參閱  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md)   
 [類型的視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)