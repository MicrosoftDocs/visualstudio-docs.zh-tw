---
title: TYPE_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 12102c297c34649c753cf1c811994f9e750b9605
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435687"
---
# <a name="typeinfo"></a>TYPE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此結構指定的各種欄位的類型的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
struct _tagTYPE_INFO_UNION {  
   dwTYPE_KIND dwKind;  
   union {  
      METADATA_TYPE typeMeta;  
      PDB_TYPE      typePdb;  
      BUILT_TYPE    typeBuilt;  
      DWORD         unused;  
   } type;  
} TYPE_INFO;  
```  
  
```csharp  
public struct TYPE_INFO {  
   public uint   dwKind;  
   public IntPtr unionmember;  
};  
```  
  
#### <a name="parameters"></a>參數  
 dwKind  
 值，以從[dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)列舉，決定如何解譯聯集。  
  
 type.typeMeta  
 [C++只]包含[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)結構，如果`dwKind`是`TYPE_KIND_METADATA`。  
  
 type.typePdb  
 [C++只]包含[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)結構，如果`dwKind`是`TYPE_KIND_PDB`。  
  
 type.typeBuilt  
 [C++只]包含[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)結構，如果`dwKind`是`TYPE_KIND_BUILT`。  
  
 type.unused  
 未使用的填補。  
  
 類型  
 聯集的名稱。  
  
 unionmember  
 [C#只]封送處理為適當的結構類型根據`dwKind`。  
  
## <a name="remarks"></a>備註  
 此結構會傳遞至[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)填滿其中的方法。 結構的內容的解譯方式根據`dwKind`欄位。  
  
> [!NOTE]
> [C++只]如果`dwKind`equals `TYPE_KIND_BUILT`，然後才釋出基礎[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件終結時`TYPE_INFO`結構。 藉由呼叫 `typeInfo.type.typeBuilt.pUnderlyingField->Release()` 即可達到此目的。  
  
 [C#只]下表顯示如何解譯`unionmember`的每一種類型的成員。 此範例會示範如何做到這點一種型別。  
  
|`dwKind`|`unionmember` 解譯為|  
|--------------|----------------------------------|  
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|  
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|  
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|  
  
## <a name="example"></a>範例  
 此範例示範如何解譯`unionmember`隸屬`TYPE_INFO`C# 中的結構。 此範例示範解譯只能有一個類型 (`TYPE_KIND_METADATA`)，但其他完全相同的方式進行解譯。  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(TYPE_INFO ti)  
        {  
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)  
            {  
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,  
                                               typeof(METADATA_TYPE));  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
