---
title: IEEVisualizerDataProvider::SetObjectForVisualizer |Microsoft 文件
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
ms.openlocfilehash: 0d1a6272f8a04316c8695f301d5c45512b05f2d3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120724"
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
 [out]如果將物件時發生錯誤，這個字串會保留錯誤訊息。  
  
 `pException`  
 [out]如果發生錯誤，此物件會保存的例外狀況資訊。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這是由實作器決定如何傳回錯誤資訊。 不過，它可能會有些呼叫端可能僅以查看例外狀況物件是否已傳回有知道查詢時，發生錯誤，因此如果發生錯誤，這個方法一律會傳回例外狀況物件。 如果呼叫端想要進行，應該也提供錯誤字串使用它。  
  
## <a name="see-also"></a>另請參閱  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)