---
title: IEEVisualizerDataProvider::SetObjectForVisualizer |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f02f90ce8325a0ba75c31904a689e84705a5273a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866164"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
這個方法會變更視覺化檢視表示的物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetObjectForVisualizer(  
   IDebugObject*  pNewObject,  
   BSTR*          error,  
   IDebugObject** pException  
);  
```  
  
```csharp  
int SetObjectForVisualizer(  
   IDebugObject     pNewObject,  
   out string       error,  
   out IDebugObject pException  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pNewObject`  
 [in]要設定的物件。  
  
 `error`  
 [out]如果將物件設定時發生錯誤，這個字串會保留錯誤訊息。  
  
 `pException`  
 [out]如果發生錯誤，此物件會保存的例外狀況資訊。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 它是由實作者決定如何傳回錯誤資訊。 不過，很可能有些呼叫端可能僅查看知道如果傳回的例外狀況物件時，發生錯誤，因此如果發生錯誤，這個方法應該一律傳回例外狀況物件。 如果呼叫端想要進行，應該也提供錯誤字串使用它。  
  
## <a name="see-also"></a>另請參閱  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)