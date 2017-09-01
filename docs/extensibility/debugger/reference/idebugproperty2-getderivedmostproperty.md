---
title: IDebugProperty2::GetDerivedMostProperty | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords:
- IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
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
ms.openlocfilehash: 90e4751b335eb901cc068c82c8cee231e39c812a
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
Gets the derived-most property of a property.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetDerivedMostProperty (   
   IDebugProperty2** ppDerivedMost  
);  
```  
  
```csharp  
int GetDerivedMostProperty (   
   out IDebugProperty2 ppDerivedMost  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `ppDerivedMost`  
 [out] Returns an [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) object that represents the derived-most property.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise returns error code. Returns `S_GETDERIVEDMOST_NO_DERIVED_MOST` if there is no derived-most property to retrieve.  
  
## <a name="remarks"></a>Remarks  
 For example, if this property describes an object that implements `ClassRoot` but which is actually an instantiation of `ClassDerived` that is derived from `ClassRoot`, then this method returns an [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) object describing the `ClassDerived` object.  
  
## <a name="see-also"></a>See Also  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
