---
title: "IDebugProperty3::GetCustomViewerList | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty3::GetCustomViewerList"
helpviewer_keywords: 
  - "IDebugProperty3::GetCustomViewerList"
ms.assetid: 74490fd8-6f44-4618-beea-dab64961bb8a
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProperty3::GetCustomViewerList
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得這個屬性相關聯的自訂檢視器的清單。  
  
## 語法  
  
```cpp  
HRESULT GetCustomViewerList(  
   ULONG                celtSkip,  
   ULONG                celtRequested,  
   DEBUG_CUSTOM_VIEWER* rgViewers,  
   ULONG*               pceltFetched  
);  
```  
  
```c#  
int GetCustomViewerList(  
   uint                  celtSkip,  
   uint                  celtRequested,  
   DEBUG_CUSTOM_VIEWER[] rgViewers,  
   out uint              pceltFetched  
);  
```  
  
#### 參數  
 `celtSkip`  
 \[in\]略過的檢視器的數目而定。  
  
 `celtRequested`  
 \[in\]若要擷取的檢視器的數目 \(也會指定大小的`rgViewers`陣列\)。  
  
 `rgViewers`  
 輸入 \[、 輸出\]陣列的[DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)結構，以填入。  
  
 `pceltFetched`  
 \[\] out「 檢視器傳回實際數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 若要支援型別視覺化檢視，這個方法會傳送呼叫至[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)方法。  如果運算式評估工具也支援自訂的檢視器，這個屬性的型別，這個方法可以將適當的自訂檢閱者共處附加至清單。  
  
 請參閱[類型的視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)如需詳細資訊，在型別視覺化檢視和自訂的檢視器之間的差異。  
  
## 範例  
 下列範例會示範如何實作這個方法，如 **CProperty** 物件，公開 \(expose\) [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)介面。  
  
```cpp#  
STDMETHODIMP CProperty::GetCustomViewerList(ULONG celtSkip, ULONG celtRequested, DEBUG_CUSTOM_VIEWER* prgViewers, ULONG* pceltFetched)  
{  
    if (NULL == prgViewers)  
    {  
        return E_POINTER;  
    }  
  
    if (GetVisualizerService())  
    {  
        return m_pIEEVisualizerService->GetCustomViewerList(celtSkip, celtRequested, prgViewers, pceltFetched);  
    }  
    else  
    {  
        return E_NOTIMPL;  
    }  
}  
```  
  
## 請參閱  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)   
 [類型的視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)