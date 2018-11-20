---
title: IEEVisualizerServiceProvider::CreateVisualizerService |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4cc37f31de5e616dbc7497cb23f9f14b73610038
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807630"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個方法會建立視覺化檢視服務。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateVisualizerService(  
   IDebugBinder*              binder,  
   IDebugSymbolProvider*      pSymProv,  
   IDebugAddress*             pAddress,  
   IEEVisualizerDataProvider* dataProvider,  
   IEEVisualizerService**     ppService  
);  
```  
  
```csharp  
int CreateVisualizerService(  
   IDebugBinder binder,  
   IDebugSymbolProvider      pSymProv,  
   IDebugAddress             pAddress,  
   IEEVisualizerDataProvider dataProvider,  
   out IEEVisualizerService  ppService  
);  
```  
  
#### <a name="parameters"></a>參數  
 `binder`  
 [in][IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)物件傳遞給[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)。  
  
 `pSymProv`  
 [in][IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)物件傳遞給`IDebugParsedExpression::EvaluateSync`。  
  
 `pAddress`  
 [in][IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)物件傳遞給`IDebugParsedExression::EvaluateSync`。  
  
 `dataProvider`  
 [in]物件，實作[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) （由運算式評估工具提供） 的介面。  
  
 `ppService`  
 [out]已建立的服務。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 `binder`， `pSymProv`，並`pAddress`參數所傳遞至`IDebugParsedExpression::EvaluateSync`方法。 `CreateVisualizerService` 要呼叫只能從`IDebugParsedExpression::EvaluateSync`一部分的運算式評估工具支援的類型視覺化檢視。  
  
## <a name="see-also"></a>另請參閱  
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

