---
title: IDebugProperty2::SetValueAsReference | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
caps.latest.revision: 9
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
ms.openlocfilehash: 58cc520d773d65cc3eba0588c2b8763079019018
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
Sets the value of this property to the value of the given reference.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetValueAsReference(  
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```csharp  
int SetValueAsReference(  
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `rgpArgs`  
 [in] An array of arguments to pass to the managed code property setter. If the property setter does not take arguments or if this [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) object does not refer to such a property setter, `rgpArgs` should be a null value. This parameter is typically a null value.  
  
 `dwArgCount`  
 [in] The number of arguments in the `rgpArgs` array.  
  
 `pValue`  
 [in] A reference, in the form of an [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) object, to the value to use to set this property.  
  
 `dwTimeout`  
 [in] How long to take to set the value, in milliseconds. A typical value is `INFINITE`. This affects the length of time that any possible evaluation can take.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise returns an error code, typically one of the following:  
  
|Error|Description|  
|-----------|-----------------|  
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|Setting the value from a reference is not supported.|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|The value cannot be set, as this property refers to a method.|  
|`E_SETVALUE_VALUE_IS_READONLY`|The value is read-only and cannot be set.|  
|`E_NOTIMPL`|The method is not implemented.|  
  
## <a name="see-also"></a>See Also  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
