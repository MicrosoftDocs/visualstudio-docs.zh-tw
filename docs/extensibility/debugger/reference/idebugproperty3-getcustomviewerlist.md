---
title: IDebugProperty3::GetCustomViewerList |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty3::GetCustomViewerList
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerList
ms.assetid: 74490fd8-6f44-4618-beea-dab64961bb8a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a98a7ca4b2f1dcf25728bd0d2e3778be2d70ada
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugproperty3getcustomviewerlist"></a>IDebugProperty3::GetCustomViewerList
取得這個屬性與相關聯的自訂檢視器的清單。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCustomViewerList(  
   ULONG                celtSkip,  
   ULONG                celtRequested,  
   DEBUG_CUSTOM_VIEWER* rgViewers,  
   ULONG*               pceltFetched  
);  
```  
  
```csharp  
int GetCustomViewerList(  
   uint                  celtSkip,  
   uint                  celtRequested,  
   DEBUG_CUSTOM_VIEWER[] rgViewers,  
   out uint              pceltFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celtSkip`  
 [in]略過的檢視器的數目。  
  
 `celtRequested`  
 [in]要擷取的檢視器的數目 (也會指定的大小`rgViewers`陣列)。  
  
 `rgViewers`  
 [in、 out]陣列[DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)要填入結構。  
  
 `pceltFetched`  
 [out]檢視器傳回的實際數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 若要支援類型的視覺化檢視，這個方法會呼叫轉寄[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)方法。 如果運算式評估工具也會支援這個屬性的類型的自訂檢視器，這個方法可以將適當的自訂檢視器附加至清單。  
  
 請參閱[類型視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)如類型視覺化檢視和自訂檢視器之間的差異的詳細資訊。  
  
## <a name="example"></a>範例  
 下列範例示範如何實作這個方法來**CProperty**公開物件[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)介面。  
  
```cpp  
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
  
## <a name="see-also"></a>另請參閱  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)   
 [類型視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)