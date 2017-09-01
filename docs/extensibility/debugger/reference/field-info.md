---
title: FIELD_INFO | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
caps.latest.revision: 14
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
ms.openlocfilehash: 749381a752521bcf728ecf1fb88583bdcbabbb00
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="fieldinfo"></a>FIELD_INFO
This structure describes a local variable, parameter, or other field.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _tagFieldInfo {   
   FIELD_INFO_FIELDS dwFields;  
   BSTR              bstrFullName;  
   BSTR              bstrName;  
   BSTR              bstrType;  
   FIELD_MODIFIERS   dwModifiers;  
} FIELD_INFO;  
```  
  
```csharp  
public struct FIELD_INFO {  
   public uint   dwFields;  
   public string bstrFullName;  
   public string bstrName;  
   public string bstrType;  
   public uint   dwModifiers;  
};  
```  
  
## <a name="members"></a>Members  
 dwFields  
 A combination of flags from the [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) enumeration that specifies which members are filled in.  
  
 bstrFullName  
 The full name of the field.  
  
 bstrName  
 The short name of the field.  
  
 bstrType  
 The type of the field.  
  
 dwModifiers  
 A combination of flags from the [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) enumeration that describes the field.  
  
## <a name="remarks"></a>Remarks  
 This structure is passed to the [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) method where it is filled in.  
  
## <a name="requirements"></a>Requirements  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>See Also  
 [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
