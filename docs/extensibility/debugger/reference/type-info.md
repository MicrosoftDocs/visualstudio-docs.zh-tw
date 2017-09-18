---
title: "TYPE_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TYPE_INFO"
helpviewer_keywords: 
  - "TYPE_INFO 結構"
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# TYPE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個結構會指定不同的欄位型別的相關資訊。  
  
## 語法  
  
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
  
```c#  
public struct TYPE_INFO {  
   public uint   dwKind;  
   public IntPtr unionmember;  
};  
```  
  
#### 參數  
 dwKind  
 介於[dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)列舉型別會決定如何解譯聯集。  
  
 type.typeMeta  
 \[只有 c \+ \+\]Contains a [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md) structure if `dwKind` is `TYPE_KIND_METADATA`.  
  
 type.typePdb  
 \[只有 c \+ \+\]Contains a [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md) structure if `dwKind` is `TYPE_KIND_PDB`.  
  
 type.typeBuilt  
 \[只有 c \+ \+\]Contains a [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md) structure if `dwKind` is `TYPE_KIND_BUILT`.  
  
 type.unused  
 未使用的填補。  
  
 type  
 聯集的名稱。  
  
 unionmember  
 \[C\# 只\]這為適當的結構的型別為基礎的封送處理`dwKind`。  
  
## 備註  
 這個結構會傳遞至[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)填滿其中的方法。  結構的內容解譯的方式根據`dwKind`欄位。  
  
> [!NOTE]
>  \[只有 c \+ \+\]如果`dwKind`等於`TYPE_KIND_BUILT`，那麼就必須釋放基礎[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件當終結`TYPE_INFO`結構。  這是藉由呼叫`typeInfo.type.typeBuilt.pUnderlyingField->Release()`。  
  
 \[C\# 只\]下表顯示如何解譯`unionmember`每種類型的成員。  此範例顯示如何這麼做是一種型別。  
  
|`dwKind`|`unionmember`解譯為|  
|--------------|----------------------|  
|`TYPE_KIND_METADATA`|[METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|  
|`TYPE_KIND_PDB`|[PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|  
|`TYPE_KIND_BUILT`|[BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)|  
  
## 範例  
 這個範例會示範如何解譯`unionmember`成員的`TYPE_INFO` C\# 中的結構。  這個範例會顯示解譯只有一個型別 \(`TYPE_KIND_METADATA`\)，但其他人會被解譯方式完全相同。  
  
```c#  
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
  
## 需求  
 標頭: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)