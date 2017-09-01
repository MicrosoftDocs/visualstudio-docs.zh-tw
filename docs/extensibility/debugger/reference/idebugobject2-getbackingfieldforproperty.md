---
title: IDebugObject2::GetBackingFieldForProperty | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
caps.latest.revision: 7
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
ms.openlocfilehash: efc582a0eaf5a4e3ccfb0f976ce7dbc60d665f9a
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Gets the field or variable (if any) that may be backing the property represented by this object.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```csharp  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `ppObject`  
 [out] An [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) object describing the backing field.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns S_OK; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 The [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) object represents a managed code class property, that is, a method with a get and/or set accessor. Such properties generally require a variable to contain the value manipulated by the property. This variable is known as the backing field. If there is no backing field for the object, then make sure to return a null value: some callers may not pay attention to the return value but will instead look to see if a null value was returned in `ppObject`.  
  
## <a name="see-also"></a>See Also  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
