---
title: IEEVisualizerDataProvider::GetNewObjectForVisualizer |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEVisualizerDataProvider::GetNewObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::GetNewObjectForVisualizer method
ms.assetid: a898d549-4898-4fde-aad1-e8bb89129652
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4e0f9ad21b14ef3999c115966ff387f0e4dcbf58
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49935337"
---
# <a name="ieevisualizerdataprovidergetnewobjectforvisualizer"></a>IEEVisualizerDataProvider::GetNewObjectForVisualizer
這個方法會取得新物件的視覺化檢視。 這個方法一律會建立新的物件，從現有的物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetNewObjectForVisualizer(  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int GetNewObjectForVisualizer(  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppObject`  
 [out]新的物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 `This method` 重新評估的物件，目前是代表，然後傳回結果做為新的物件。 評估的結果，將會更新現有的物件。  
  
## <a name="see-also"></a>另請參閱  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)