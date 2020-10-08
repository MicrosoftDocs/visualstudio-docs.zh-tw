---
title: TYPE_INFO |Microsoft Docs
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
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2020
ms.locfileid: "91838499"
---
# <a name="type_info"></a>TYPE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此結構會指定欄位類型的各種資訊。  
  
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
 [DwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)列舉中的值，可決定如何解讀聯集。  
  
 輸入. typeMeta  
 [僅限 c + +]如果為，則包含 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) 結構 `dwKind` `TYPE_KIND_METADATA` 。  
  
 輸入. typePdb  
 [僅限 c + +]如果為，則包含 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) 結構 `dwKind` `TYPE_KIND_PDB` 。  
  
 輸入. typeBuilt  
 [僅限 c + +]如果為，則包含 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) 結構 `dwKind` `TYPE_KIND_BUILT` 。  
  
 類型。未使用  
 未使用的填補。  
  
 type  
 聯集的名稱。  
  
 unionmember  
 [僅限 c #]根據，將此封送處理至適當的結構類型 `dwKind` 。  
  
## <a name="remarks"></a>備註  
 此結構會傳遞至其填入的 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) 方法。 如何解讀結構的內容是以欄位為基礎 `dwKind` 。  
  
> [!NOTE]
> [僅限 c + +]如果 `dwKind` 等於 `TYPE_KIND_BUILT` ，則當終結結構時，必須釋放基礎 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 物件 `TYPE_INFO` 。 藉由呼叫 `typeInfo.type.typeBuilt.pUnderlyingField->Release()` 即可達到此目的。  
  
 [僅限 c #]下表說明如何解讀 `unionmember` 每種類型的成員。 此範例會示範如何針對一種類型來完成這項操作。  
  
|`dwKind`|`unionmember` 解釋為|  
|--------------|----------------------------------|  
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|  
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|  
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|  
  
## <a name="example"></a>範例  
 此範例示範如何 `unionmember` `TYPE_INFO` 在 c # 中解讀結構的成員。 這個範例只會示範將一個型別 (`TYPE_KIND_METADATA`) ，但是其他人會以完全相同的方式來解讀。  
  
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
 標頭： sh. h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
