---
title: IDebugMethodField::EnumParameters |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 674f2cc7160ace49f4fc8b5333fc3b951a7ccc8b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53823175"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
建立的列舉程式方法的參數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumParameters(   
   IEnumDebugFields** ppParams  
);  
```  
  
```csharp  
int EnumParameters(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppParams`  
 [out]會傳回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)方法表示的參數清單的物件; 如果沒有任何參數，否則會傳回 null 值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK，或如果沒有任何參數，則傳回 S_FALSE。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 每個項目是[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件，代表不同類型的參數。 呼叫[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)判斷完全代表哪種參數物件的每個物件上的方法。  
  
 參數會包含其變數名稱和型別。 在類別方法的第一個參數通常是 「 this 」 指標。  
  
 如果只需要一個參數的類型時，呼叫[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)