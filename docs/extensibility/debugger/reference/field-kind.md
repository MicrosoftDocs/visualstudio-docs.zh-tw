---
title: FIELD_KIND |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- FIELD_KIND
helpviewer_keywords:
- FIELD_KIND enumeration
ms.assetid: fd522b9c-52e2-42fa-939d-343347d5c3b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 35a603310986f42141a04f38c7ce26db0d7326fe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="fieldkind"></a>FIELD_KIND
指定欄位中所包含的類型[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_FIELD_KIND {   
   FIELD_KIND_NONE       = 0x00000000,  
  
   // Type of field  
   FIELD_KIND_TYPE       = 0x00000001,  
   FIELD_KIND_SYMBOL     = 0x00000002,  
  
   // Storage type of the field  
   FIELD_TYPE_PRIMITIVE  = 0x00000010,  
   FIELD_TYPE_STRUCT     = 0x00000020,  
   FIELD_TYPE_CLASS      = 0x00000040,  
   FIELD_TYPE_INTERFACE  = 0x00000080,  
   FIELD_TYPE_UNION      = 0x00000100,  
   FIELD_TYPE_ARRAY      = 0x00000200,  
   FIELD_TYPE_METHOD     = 0x00000400,  
   FIELD_TYPE_BLOCK      = 0x00000800,  
   FIELD_TYPE_POINTER    = 0x00001000,  
   FIELD_TYPE_ENUM       = 0x00002000,  
   FIELD_TYPE_LABEL      = 0x00004000,  
   FIELD_TYPE_TYPEDEF    = 0x00008000,  
   FIELD_TYPE_BITFIELD   = 0x00010000,  
   FIELD_TYPE_NAMESPACE  = 0x00020000,  
   FIELD_TYPE_MODULE     = 0x00040000,  
   FIELD_TYPE_DYNAMIC    = 0x00080000,  
   FIELD_TYPE_PROP       = 0x00100000,  
   FIELD_TYPE_INNERCLASS = 0x00200000,  
   FIELD_TYPE_REFERENCE  = 0x00400000,  
   FIELD_TYPE_EXTENDED   = 0x00800000,  
  
   // Specific information about symbols  
   FIELD_SYM_MEMBER      = 0x01000000,  
   FIELD_SYM_LOCAL       = 0x02000000,  
   FIELD_SYM_PARAM       = 0x04000000,  
   FIELD_SYM_THIS        = 0x08000000,  
   FIELD_SYM_GLOBAL      = 0x10000000,  
   FIELD_SYM_PROP_GETTER = 0x20000000,  
   FIELD_SYM_PROP_SETTER = 0x40000000,  
   FIELD_SYM_EXTENDED    = 0x80000000,  
  
   FIELD_KIND_MASK       = 0x0000000f,  
   FIELD_TYPE_MASK       = 0x00fffff0,  
   FIELD_SYM_MASK        = 0xff000000,  
  
   FIELD_KIND_ALL        = 0xffffffff  
};  
typedef DWORD FIELD_KIND;  
```  
  
```csharp  
public enum enum_FIELD_KIND {  
   FIELD_KIND_NONE       = 0x00000000,  
  
   // Type of field  
   FIELD_KIND_TYPE       = 0x00000001,  
   FIELD_KIND_SYMBOL     = 0x00000002,  
  
   // Storage type of the field  
   FIELD_TYPE_PRIMITIVE  = 0x00000010,  
   FIELD_TYPE_STRUCT     = 0x00000020,  
   FIELD_TYPE_CLASS      = 0x00000040,  
   FIELD_TYPE_INTERFACE  = 0x00000080,  
   FIELD_TYPE_UNION      = 0x00000100,  
   FIELD_TYPE_ARRAY      = 0x00000200,  
   FIELD_TYPE_METHOD     = 0x00000400,  
   FIELD_TYPE_BLOCK      = 0x00000800,  
   FIELD_TYPE_POINTER    = 0x00001000,  
   FIELD_TYPE_ENUM       = 0x00002000,  
   FIELD_TYPE_LABEL      = 0x00004000,  
   FIELD_TYPE_TYPEDEF    = 0x00008000,  
   FIELD_TYPE_BITFIELD   = 0x00010000,  
   FIELD_TYPE_NAMESPACE  = 0x00020000,  
   FIELD_TYPE_MODULE     = 0x00040000,  
   FIELD_TYPE_DYNAMIC    = 0x00080000,  
   FIELD_TYPE_PROP       = 0x00100000,  
   FIELD_TYPE_INNERCLASS = 0x00200000,  
   FIELD_TYPE_REFERENCE  = 0x00400000,  
   FIELD_TYPE_EXTENDED   = 0x00800000,  
  
   // Specific information about symbols  
   FIELD_SYM_MEMBER      = 0x01000000,  
   FIELD_SYM_LOCAL       = 0x02000000,  
   FIELD_SYM_PARAM       = 0x04000000,  
   FIELD_SYM_THIS        = 0x08000000,  
   FIELD_SYM_GLOBAL      = 0x10000000,  
   FIELD_SYM_PROP_GETTER = 0x20000000,  
   FIELD_SYM_PROP_SETTER = 0x40000000,  
   FIELD_SYM_EXTENDED    = 0x80000000,  
  
   FIELD_KIND_MASK       = 0x0000000f,  
   FIELD_TYPE_MASK       = 0x00fffff0,  
   FIELD_SYM_MASK        = 0xff000000,  
  
   FIELD_KIND_ALL        = 0xffffffff  
};  
```  
  
## <a name="members"></a>成員  
 FIELD_KIND_TYPE  
 表示欄位是只在型別。  
  
 FIELD_KIND_SYMBOL  
 表示欄位是一種符號，以類型、 名稱和其他資訊。  
  
 FIELD_TYPE_PRIMITIVE  
 表示欄位的基本資料類型。  
  
 FIELD_TYPE_STRUCT  
 表示欄位是一種結構。  
  
 FIELD_TYPE_CLASS  
 表示欄位的類別。  
  
 FIELD_TYPE_INTERFACE  
 表示欄位是一種介面。  
  
 FIELD_TYPE_UNION  
 表示欄位是等位。  
  
 FIELD_TYPE_ARRAY  
 表示欄位的陣列。  
  
 FIELD_TYPE_METHOD  
 表示欄位是一種方法。  
  
 FIELD_TYPE_BLOCK  
 表示欄位是一個區塊。  
  
 FIELD_TYPE_POINTER  
 表示欄位的指標。  
  
 FIELD_TYPE_ENUM  
 表示欄位是列舉的資料型別。  
  
 FIELD_TYPE_LABEL  
 表示欄位的標籤。  
  
 FIELD_TYPE_TYPEDEF  
 表示欄位的 typedef。  
  
 FIELD_TYPE_BITFIELD  
 表示欄位是位元欄位。  
  
 FIELD_TYPE_NAMESPACE  
 表示欄位是命名空間。  
  
 FIELD_TYPE_MODULE  
 表示欄位是一個模組。  
  
 FIELD_TYPE_DYNAMIC  
 表示欄位是動態的。  
  
 FIELD_TYPE_PROP  
 表示欄位的屬性。  
  
 FIELD_TYPE_INNERCLASS  
 表示欄位是內部的類別。  
  
 FIELD_TYPE_REFERENCE  
 表示欄位的參考。  
  
 FIELD_TYPE_EXTENDED  
 保留供未來使用。  
  
 FIELD_SYM_MEMBER  
 表示欄位的成員。  
  
 FIELD_SYM_LOCAL  
 表示本機欄位。  
  
 FIELD_SYM_PARAMETER  
 表示欄位是參數。  
  
 FIELD_SYM_THIS  
 表示欄位是"this"指標。  
  
 FIELD_SYM_GLOBAL  
 表示欄位是全域的。  
  
 FIELD_SYM_PROP_GETTER  
 表示欄位擷取屬性。  
  
 FIELD_SYM_PROP_SETTER  
 表示欄位會設定屬性。  
  
 FIELD_SYM_EXTENDED  
 保留供未來使用。  
  
 FIELD_KIND_MASK  
 表示遮罩的欄位類型。  
  
 FIELD_TYPE_MASK  
 表示遮罩的欄位類型。  
  
 FIELD_SYM_MASK  
 表示遮罩的符號資訊。  
  
## <a name="remarks"></a>備註  
 從呼叫傳回[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)方法。  
  
 根據欄位中，類型[QueryInterface](/cpp/atl/queryinterface)可上呼叫[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)更特定的介面表單的介面。 例如，如果[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)傳回`FIELD_TYPE_METHOD`，您就可以呼叫`QueryInterface`i`DebugField`取得[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)介面。  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)