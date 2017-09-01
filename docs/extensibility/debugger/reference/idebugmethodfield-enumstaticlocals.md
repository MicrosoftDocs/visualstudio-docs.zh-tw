---
title: IDebugMethodField::EnumStaticLocals | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
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
ms.openlocfilehash: b1a34ce11a6d1291d8f33cce5d95f61ed13b8fec
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugmethodfieldenumstaticlocals"></a>IDebugMethodField::EnumStaticLocals
Creates an enumerator for static local variables of the method.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT EnumStaticLocals(   
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumStaticLocals(  
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `ppLocals`  
 [out] Returns an [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) object representing the list of static locals. Returns a null value if there are no static locals.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns S_OK or returns S_FALSE if there are no static locals. Otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 Each element is an [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) object representing different types of static locals. Call the [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) method on each object to determine exactly what kind of static local the object represents.  
  
## <a name="see-also"></a>See Also  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
