---
title: IEEVisualizerDataProvider：： SetObjectForVisualizer |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d20164e31f8c42b7099f99ff34ac120319a2def1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62540260"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個方法會變更視覺化程式所代表的物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetObjectForVisualizer(  
   IDebugObject*  pNewObject,  
   BSTR*          error,  
   IDebugObject** pException  
);  
```  
  
```csharp  
int SetObjectForVisualizer(  
   IDebugObject     pNewObject,  
   out string       error,  
   out IDebugObject pException  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pNewObject`  
 在要設定的物件。  
  
 `error`  
 擴展如果設定物件時發生錯誤，此字串會保存錯誤訊息。  
  
 `pException`  
 擴展如果發生錯誤，此物件會保存例外狀況資訊。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 由實施者決定如何傳回錯誤資訊。 不過，某些呼叫端可能只會查看是否傳回例外狀況物件以知道是否發生錯誤，因此，如果發生錯誤，這個方法應該一律傳回例外狀況物件。 如果呼叫端想要使用它，也應該提供錯誤字串。  
  
## <a name="see-also"></a>另請參閱  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
