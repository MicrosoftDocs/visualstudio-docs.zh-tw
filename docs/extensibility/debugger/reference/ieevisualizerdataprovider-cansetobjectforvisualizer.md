---
title: IEEVisualizerDataProvider::CanSetObjectForVisualizer |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEVisualizerDataProvider::CanSetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::CanSetObjectForVisualizer method
ms.assetid: 70fd3c6f-2f82-43a3-993b-c1dc8aa080bf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e9a70ca947a6b794f74baec9805941c5a9610936
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825704"
---
# <a name="ieevisualizerdataprovidercansetobjectforvisualizer"></a>IEEVisualizerDataProvider::CanSetObjectForVisualizer
這個方法會判斷是否視覺化檢視可以更新它所代表的資料物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CanSetObjectForVisualizer(  
   BOOL* b  
);  
```  
  
```csharp  
int CanSetObjectForVisualizer(  
   out int b  
);  
```  
  
#### <a name="parameters"></a>參數  
 `b`  
 [out]非零值 (`TRUE`) 可以更新在視覺化檢視上的物件，如果零 (`FALSE`) 如果不行。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 物件可能無法變更，如果它繫結至唯讀的記憶體，例如。  
  
## <a name="see-also"></a>另請參閱  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)