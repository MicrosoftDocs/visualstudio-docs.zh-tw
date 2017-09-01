---
title: IDebugObject2::GetICorDebugValue | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject2::GetICorDebugValue
helpviewer_keywords:
- IDebugObject2::GetICorDebugValue method
ms.assetid: bcd4355d-3fbe-483f-bb23-a44348323c6a
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 477ce5c18672e8324667e28754810e66101e7b0c
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugobject2geticordebugvalue"></a>IDebugObject2::GetICorDebugValue
Gets a managed code object representing the value associated with this object.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `ppUnk`  
 [out] `IUnknown` interface that represents this alias. This interface can be queried for the `ICorDebugValue` interface.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns S_OK; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 The `ICorDebugValue` object is a Common Language Runtime interface that represents a value.  
  
## <a name="see-also"></a>See Also  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
