---
title: IDebugBinder3::GetEEService |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56c97e9fc7e5505578533c9e7b958a73dc8d2380
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
這個方法會傳回要求的服務。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetEEService(  
   [in] GUID        vendor,  
   [in] GUID        language,  
   [in] GUID        iid,  
   [out] IUnknown** ppService  
);  
```  
  
```csharp  
Int GetEEService(  
   Guid       vendor,  
   Guid       language,  
   Guid       iid,  
   out object ppService  
);  
```  
  
#### <a name="parameters"></a>參數  
 `vendor`  
 [in]`GUID`的供應商 （null 值是可接受）。  
  
 `language`  
 [in]`GUID` （null 值是可接受） 的語言。  
  
 `iid`  
 [in]`IID`要取得的服務。  
  
 `ppService`  
 [out]所要求的服務介面。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 傳遞`IID`如[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)介面 (`IID_IEEVisualizerServiceProvider`) 類型的視覺化檢視服務是否可用。 如果運算式評估工具，可取得[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)介面，以支援類型的視覺化檢視。 請參閱[Visualizing 和檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)如需詳細資訊。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)