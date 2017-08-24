---
title: IDebugClassField::EnumConstructors | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
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
ms.sourcegitcommit: ff8ecec19f8cab04ac2190f9a4a995766f1750bf
ms.openlocfilehash: 1d8d8e0750ec93a0d53774cc415cf5e17909fc2a
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
Creates an enumerator for the constructors for this class.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT EnumConstructors(   
   CONSTRUCTOR_ENUM   cMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```cs  
int EnumConstructors(  
   CONSTRUCTOR_ENUM     cMatch,   
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `cMatch`  
 [in] A value from the [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) enumeration that specifies the type of constructors to enumeration.  
  
 `ppEnum`  
 [out] Returns an [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) object representing the list of constructors. Returns a null value if there are no constructors.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns S_OK or returns S_FALSE if there are no constructors. Otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 Each element of the enumeration is an [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) object describing a constructor method.  
  
 The list of constructors typically does not include the default constructors supplied by a compiler.  
  
## <a name="see-also"></a>See Also  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)
