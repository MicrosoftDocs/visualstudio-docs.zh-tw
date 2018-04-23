---
title: DEBUG_ADDRESS_UNION |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0b0fcd662e3a4831b78ca55c139ce1511ea04b24
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="debugaddressunion"></a>DEBUG_ADDRESS_UNION
說明不同類型的位址。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS_UNION {  
   ADDRESS_KIND dwKind;  
   union {  
      NATIVE_ADDRESS                  addrNative;  
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;  
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;  
      METADATA_ADDRESS_METHOD         addrMethod;  
      METADATA_ADDRESS_FIELD          addrField;  
      METADATA_ADDRESS_LOCAL          addrLocal;  
      METADATA_ADDRESS_PARAM          addrParam;  
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;  
      METADATA_ADDRESS_RETVAL         addrRetVal;  
      DWORD                           unused;  
   } addr;  
} DEBUG_ADDRESS_UNION;  
```  
  
```csharp  
public struct DEBUG_ADDRESS_UNION {  
   public ADDRESS_KIND dwKind;  
   public IntPtr       unionmember;  
}  
```  
  
## <a name="terms"></a>詞彙  
 dwKind  
 中的值[ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)列舉，指定如何解譯聯集。  
  
 addr.addrNative  
 [只有 c + +]包含[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)結構如果`dwKind`= ADDRESS_KIND_NATIVE。  
  
 addr.addrThisRel  
 [只有 c + +]包含[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)結構如果`dwKind`= ADDRESS_KIND_UNMANAGED_THIS_RELATIVE。  
  
 addr.addUPhysical  
 [只有 c + +]包含[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)結構如果`dwKind`= ADDRESS_KIND_UNMANAGED_PHYSICAL。  
  
 addr.addrMethod  
 [只有 c + +]包含[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)結構如果`dwKind`= ADDRESS_KIND_METHOD。  
  
 addr.addrField  
 [只有 c + +]包含[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)結構如果`dwKind`= ADDRESS_KIND_FIELD。  
  
 addr.addrLocal  
 [只有 c + +]包含[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)結構如果`dwKind`= ADDRESS_KIND_LOCAL。  
  
 addr.addrParam  
 [只有 c + +]包含[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)結構如果`dwKind`= ADDRESS_KIND_PARAM。  
  
 addr.addrArrayElem  
 [只有 c + +]包含[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)結構如果`dwKind`= ADDRESS_KIND_ARRAYELEM。  
  
 addr.addrRetVal  
 [只有 c + +]包含[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)結構如果`dwKind`= ADDRESS_KIND_RETVAL。  
  
 addr.unused  
 [只有 c + +] 填補。  
  
 Addr  
 [只有 c + +]聯集的名稱。  
  
 unionmember  
 [僅限 C#]此值必須根據適當的結構類型封送處理`dwKind`。 如之間的關聯，請參閱 < 備註 > 一`dwKind`和等位的解釋。  
  
## <a name="remarks"></a>備註  
 這個結構是一部分[DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)結構，並代表一個位址的不同種類的數字 (`DEBUG_ADDRESS`結構填入呼叫[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)方法)。  
  
 [僅限 C#]下表顯示如何解譯`unionmember`的每一種位址的成員。 此範例會示範這基於位址的一種。  
  
|`dwKind`|`unionmember` 解譯為|  
|--------------|----------------------------------|  
|`ADDRESS_KIND_NATIVE`|[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|  
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|  
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|  
|`ADDRESS_KIND_METHOD`|[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|  
|`ADDRESS_KIND_FIELD`|[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|  
|`ADDRESS_KIND_LOCAL`|[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|  
|`ADDRESS_KIND_PARAM`|[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|  
|`ADDRESS_KIND_ARRAYELEM`|[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|  
|`ADDRESS_KIND_RETVAL`|[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|  
  
## <a name="example"></a>範例  
 這個範例示範如何解譯位址的一種 (`METADATA_ADDRESS_ARRAYELEM`) 的`DEBUG_ADDRESS_UNION`C# 中的結構。 其餘的項目可以解譯方式完全相同。  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(DEBUG_ADDRESS_UNION dau)  
        {  
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)  
            {  
                 METADATA_ADDRESS_ARRAYELEM arrayElem =  
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,  
                                 typeof(METADATA_ADDRESS_ARRAYELEM));  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)