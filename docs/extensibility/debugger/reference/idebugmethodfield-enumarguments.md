---
title: IDebugMethodField::EnumArguments |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d9fe8eb5d3eb99037f3968261434690f1abfb201
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55015923"
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
建立的每一個需要呼叫方法的引數類型的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumArguments(   
   IEnumDebugFields** ppParams  
);  
```  
  
```csharp  
int EnumArguments(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppParams`  
 [out]傳回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件，表示引數類型清單。 如果不有任何引數，則傳回 null 值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK，或如果沒有任何引數，則傳回 S_FALSE。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 每個項目是[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件，表示每個參數的類型。 呼叫[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)方法來擷取每個參數類型的相關資訊。  
  
 如果以及類型需要參數的名稱，然後呼叫[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)