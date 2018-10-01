---
title: IDebugProperty3::GetCustomViewerCount |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProperty3::GetCustomViewerCount
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerCount
ms.assetid: dc5bb3e4-dc85-46e4-98fa-c6be8583b985
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: af4a1ee246c2e04256ad5cb5b40644084e8c34ae
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497301"
---
# <a name="idebugproperty3getcustomviewercount"></a>IDebugProperty3::GetCustomViewerCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugProperty3::GetCustomViewerCount](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugproperty3-getcustomviewercount)。  
  
取得可供這個屬性的自訂檢視器的數目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCustomViewerCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCustomViewerCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pcelt`  
 [out]適用於此屬性的自訂檢視器的數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 為了支援類型視覺化檢視，這個方法會呼叫轉寄[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)方法。 如果運算式評估工具也支援自訂檢視器，這個屬性的類型，這個方法會將傳回值的自訂檢視器的數目。  
  
 如需類型視覺化檢視和自訂檢視器之間的差異的詳細資訊，請參閱[類型視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何實作這個方法，如**CProperty**公開 （expose） 的物件[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)介面。  
  
```cpp#  
STDMETHODIMP CProperty::GetCustomViewerCount(ULONG* pcelt)  
{  
    if (pcelt == NULL)  
    {  
        return E_POINTER;  
    }  
  
    if (GetVisualizerService())  
    {  
        return m_pIEEVisualizerService->GetCustomViewerCount(pcelt);  
    }  
    else  
    {  
        return E_NOTIMPL;  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)   
 [類型視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

