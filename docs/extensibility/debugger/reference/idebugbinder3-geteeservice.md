---
title: "IDebugBinder3::GetEEService |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder3::GetEEService
helpviewer_keywords: IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aa705de1871530c8f53f5b29b6040909530b6639
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
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