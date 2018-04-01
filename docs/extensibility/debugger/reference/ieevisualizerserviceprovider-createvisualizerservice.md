---
title: IEEVisualizerServiceProvider::CreateVisualizerService |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b9c34f5b11aed9ed51ca10f662ea161d792e54b6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
這個方法會建立視覺化檢視服務。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateVisualizerService(  
   IDebugBinder*              binder,  
   IDebugSymbolProvider*      pSymProv,  
   IDebugAddress*             pAddress,  
   IEEVisualizerDataProvider* dataProvider,  
   IEEVisualizerService**     ppService  
);  
```  
  
```csharp  
int CreateVisualizerService(  
   IDebugBinder binder,  
   IDebugSymbolProvider      pSymProv,  
   IDebugAddress             pAddress,  
   IEEVisualizerDataProvider dataProvider,  
   out IEEVisualizerService  ppService  
);  
```  
  
#### <a name="parameters"></a>參數  
 `binder`  
 [in][IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)物件傳遞至[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)。  
  
 `pSymProv`  
 [in][IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)物件傳遞至`IDebugParsedExpression::EvaluateSync`。  
  
 `pAddress`  
 [in][IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)物件傳遞至`IDebugParsedExression::EvaluateSync`。  
  
 `dataProvider`  
 [in]實作[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) （由運算式評估工具提供） 的介面。  
  
 `ppService`  
 [out]建立的服務。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 `binder`， `pSymProv`，和`pAddress`參數已傳遞至`IDebugParsedExpression::EvaluateSync`方法。 `CreateVisualizerService`是只會從呼叫`IDebugParsedExpression::EvaluateSync`一部分的運算式評估工具支援的類型視覺化檢視。  
  
## <a name="see-also"></a>請參閱  
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)