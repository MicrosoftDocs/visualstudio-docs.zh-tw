---
title: DEBUG_ADDRESS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
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
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: aa37858e7fc9c05a9ba86570a2df5891600399d9
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="debugaddress"></a>DEBUG_ADDRESS
This structure represents an address.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS {  
   ULONG32             ulAppDomainID;  
   GUID                guidModule;  
   _mdToken            tokClass;  
   DEBUG_ADDRESS_UNION addr;  
} DEBUG_ADDRESS;  
```  
  
```csharp  
public struct DEBUG_ADDRESS {  
   public uint                ulAppDomainID;  
   public Guid                guidModule;  
   public int                 tokClass;  
   public DEBUG_ADDRESS_UNION addr;  
}  
```  
  
## <a name="terms"></a>Terms  
 ulAppDomainID  
 The process ID.  
  
 guidModule  
 The GUID of the module that contains this address.  
  
 tokClass  
 The token identifying the class or type of this address.  
  
> [!NOTE]
>  This value is specific to a symbol provider and therefore has no general meaning other than as an identifier for a class type.  
  
 addr  
 A [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) structure, which contains a union of structures that describe the individual address types. The value `addr`.`dwKind` comes from the [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) enumeration, which explains how to interpret the union.  
  
## <a name="remarks"></a>Remarks  
 This structure is passed to the [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) method to be filled in.  
  
 **Warning [C++ only]**  
  
 If `addr.dwKind` is `ADDRESS_KIND_METADATA_LOCAL` and if `addr.addr.addrLocal.pLocal` is not a null value, then you must call `Release` on the token pointer:  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## <a name="requirements"></a>Requirements  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>See Also  
 [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
