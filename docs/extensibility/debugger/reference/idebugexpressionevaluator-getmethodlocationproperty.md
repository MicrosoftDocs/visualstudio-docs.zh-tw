---
title: IDebugExpressionEvaluator::GetMethodLocationProperty |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 612cdb579615acb7ca5b4b6a34c0c485683c4fe1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
這個方法會將方法的位置和位移轉換成記憶體位址。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetMethodLocationProperty(   
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```csharp  
int GetMethodLocationProperty(  
   string               upstrFullyQualifiedMethodPlusOffset,   
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### <a name="parameters"></a>參數  
 `upstrFullyQualifiedMethodPlusOffset`  
 [in]方法的位置和位移、 以字串表示。  
  
 `pSymbolProvider`  
 [in]符號提供者以[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)物件。  
  
 `pAddress`  
 [in]在方法中，以表示位址[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)物件。  
  
 `pBinder`  
 [in]繫結器表示為[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)物件。  
  
 `ppProperty`  
 [out]傳回[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)代表記憶體位址的介面。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 傳回的位址可以用來設定中斷點，例如。  
  
 不論名稱為何`upstrFullyQualifiedMethodPlusOffset`，這個參數可以傳遞的不完整的方法名稱。 在此情況下，選取的方法是一個內含`pAddress`。 這個參數的解譯方式，是由運算式評估工具及它所支援的語言實作。  
  
## <a name="see-also"></a>請參閱  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)