---
title: IDebugBinder::ResolveRuntimeType |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder::ResolveRuntimeType
helpviewer_keywords:
- IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e2bfca2c360741b92c3a7ce3c4773671d8bf4d6f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928122"
---
# <a name="idebugbinderresolveruntimetype"></a>IDebugBinder::ResolveRuntimeType
這個方法會判斷物件的執行階段型別。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ResolveRuntimeType(   
   IDebugObject* pObject,  
   IDebugField** ppResolved  
);  
```  
  
```csharp  
int ResolveRuntimeType(  
   IDebugObject     pObject,   
   out IDebugField  ppResolved  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pObject`  
 [in][IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)進行解析。  
  
 `ppResolved`  
 [out]傳回的物件做為類型[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 物件的執行階段類型不一定知道在編譯時期。 比方說，使用多型，引數可以傳遞至函式作為其基底類別，例如按鈕類別。 實際引數可能衍生的類別，例如選項按鈕類別。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)