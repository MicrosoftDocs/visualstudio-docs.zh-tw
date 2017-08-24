---
title: IDebugContainerField::EnumFields | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
caps.latest.revision: 10
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
ms.openlocfilehash: 9fec1b721cdfc204a410d9943ee6235fa2803224
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
Creates an enumerator for the fields of the container.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT EnumFields(   
   FIELD_KIND         dwKindFilter,  
   FIELD_MODIFIERS    dwModifiersFilter,  
   LPCOLESTR          pszNameFilter,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```cs  
int EnumFields(  
   enum_ FIELD_KIND      dwKindFilter,   
   enum_ FIELD_MODIFIERS dwModifiersFilter,   
   string                pszNameFilter,   
   NAME_MATCH            nameMatch,   
   out IEnumDebugFields  ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `dwKindFilter`  
 [in] A combination of [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) constants that select the fields to be enumerated. Field kinds can describe storage types, such as class or primitive, or specific information, such as local, parameter, or "this" pointer.  
  
 `dwModifiersFilter`  
 [in] A combination of [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) constants that select the fields to be enumerated. Field modifiers can be access permissions, such as public or private, or storage information, such as virtual, static, or final.  
  
 `pszNameFilter`  
 [in] The name of the field to be enumerated. This can be a null value if all fields are to be returned.  
  
 `nameMatch`  
 [in] A value from the [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) enumeration that controls whether searching is case-sensitive or not.  
  
 `ppEnum`  
 [out] Returns an [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) object representing the list of fields. Returns a null value if there are no fields.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns S_OK or S_FALSE if there are no fields. Otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 The `dwKindFilter`, `dwModifiersFilter`, and `pszNameFilter` parameters can be combined, for example, to select all public virtual methods named "MyMethod".  
  
## <a name="see-also"></a>See Also  
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
