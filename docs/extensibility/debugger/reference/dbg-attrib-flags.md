---
description: 描述 IDebugProperty2 或 IDebugReference2 介面的各種屬性。
title: DBG_ATTRIB_FLAGS |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DBG_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS enumerations
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aba733cd1e8ff05adac0cd538da79e4d437e6f60
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096469"
---
# <a name="dbg_attrib_flags"></a>DBG_ATTRIB_FLAGS
描述 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 或 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 介面的各種屬性。 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構的成員。

## <a name="syntax"></a>語法

```cpp
#define DBG_ATTRIB_NONE                 0x0000000000000000,
#define DBG_ATTRIB_ALL                  0x00000000ffffffff,

// Attributes about the object itself

#define DBG_ATTRIB_OBJ_IS_EXPANDABLE    0x0000000000000001,
#define DBG_ATTRIB_OBJ_HAS_ID           0x0000000000000002,
#define DBG_ATTRIB_OBJ_CAN_HAVE_ID      0x0000000000000004,

// Attributes about the value of the object

#define DBG_ATTRIB_VALUE_READONLY       0x0000000000000010,
#define DBG_ATTRIB_VALUE_ERROR          0x0000000000000020,
#define DBG_ATTRIB_VALUE_SIDE_EFFECT    0x0000000000000040,
#define DBG_ATTRIB_OVERLOADED_CONTAINER 0x0000000000000080,
#define DBG_ATTRIB_VALUE_BOOLEAN        0x0000000000000100,
#define DBG_ATTRIB_VALUE_BOOLEAN_TRUE   0x0000000000000200,
#define DBG_ATTRIB_VALUE_INVALID        0x0000000000000400,
#define DBG_ATTRIB_VALUE_NAT            0x0000000000000800,
#define DBG_ATTRIB_VALUE_AUTOEXPANDED   0x0000000000001000,
#define DBG_ATTRIB_VALUE_TIMEOUT        0x0000000000002000,
#define DBG_ATTRIB_VALUE_RAW_STRING     0x0000000000004000,
#define DBG_ATTRIB_VALUE_CUSTOM_VIEWER  0x0000000000008000,

// Attributes about field access types for the object

#define DBG_ATTRIB_ACCESS_NONE          0x0000000000010000,
#define DBG_ATTRIB_ACCESS_PUBLIC        0x0000000000020000,
#define DBG_ATTRIB_ACCESS_PRIVATE       0x0000000000040000,
#define DBG_ATTRIB_ACCESS_PROTECTED     0x0000000000080000,
#define DBG_ATTRIB_ACCESS_FINAL         0x0000000000100000,
#define DBG_ATTRIB_ACCESS_ALL           0x00000000001f0000,

// Attributes for the storage types of the object

#define DBG_ATTRIB_STORAGE_NONE         0x0000000001000000,
#define DBG_ATTRIB_STORAGE_GLOBAL       0x0000000002000000,
#define DBG_ATTRIB_STORAGE_STATIC       0x0000000004000000,
#define DBG_ATTRIB_STORAGE_REGISTER     0x0000000008000000,
#define DBG_ATTRIB_STORAGE_ALL          0x000000000f000000,

// Attributes for the type modifiers on the object

#define DBG_ATTRIB_TYPE_NONE            0x0000000100000000,
#define DBG_ATTRIB_TYPE_VIRTUAL         0x0000000200000000,
#define DBG_ATTRIB_TYPE_CONSTANT        0x0000000400000000,
#define DBG_ATTRIB_TYPE_SYNCHRONIZED    0x0000000800000000,
#define DBG_ATTRIB_TYPE_VOLATILE        0x0000001000000000,
#define DBG_ATTRIB_TYPE_ALL             0x0000001f00000000,

// Attributes that describe the type of object

#define DBG_ATTRIB_DATA                 0x0000010000000000,
#define DBG_ATTRIB_METHOD               0x0000020000000000,
#define DBG_ATTRIB_PROPERTY             0x0000040000000000,
#define DBG_ATTRIB_CLASS                0x0000080000000000,
#define DBG_ATTRIB_BASECLASS            0x0000100000000000,
#define DBG_ATTRIB_INTERFACE            0x0000200000000000,
#define DBG_ATTRIB_INNERCLASS           0x0000400000000000,
#define DBG_ATTRIB_MOSTDERIVED          0x0000800000000000,
#define DBG_ATTRIB_CHILD_ALL            0x0000ff0000000000,

// Miscellaneous attributes

#define DBG_ATTRIB_MULTI_CUSTOM_VIEWERS 0x0001000000000000

typedef UINT64 DBG_ATTRIB_FLAGS;
```

```csharp
public const int DBG_ATTRIB_NONE                 = 0x0000000000000000,
public const int DBG_ATTRIB_ALL                  = 0x00000000ffffffff,

// Attributes about the object itself

public const int DBG_ATTRIB_OBJ_IS_EXPANDABLE    = 0x0000000000000001,
public const int DBG_ATTRIB_OBJ_HAS_ID           = 0x0000000000000002,
public const int DBG_ATTRIB_OBJ_CAN_HAVE_ID      = 0x0000000000000004,

// Attributes about the value of the object

public const int DBG_ATTRIB_VALUE_READONLY       = 0x0000000000000010,
public const int DBG_ATTRIB_VALUE_ERROR          = 0x0000000000000020,
public const int DBG_ATTRIB_VALUE_SIDE_EFFECT    = 0x0000000000000040,
public const int DBG_ATTRIB_OVERLOADED_CONTAINER = 0x0000000000000080,
public const int DBG_ATTRIB_VALUE_BOOLEAN        = 0x0000000000000100,
public const int DBG_ATTRIB_VALUE_BOOLEAN_TRUE   = 0x0000000000000200,
public const int DBG_ATTRIB_VALUE_INVALID        = 0x0000000000000400,
public const int DBG_ATTRIB_VALUE_NAT            = 0x0000000000000800,
public const int DBG_ATTRIB_VALUE_AUTOEXPANDED   = 0x0000000000001000,
public const int DBG_ATTRIB_VALUE_TIMEOUT        = 0x0000000000002000,
public const int DBG_ATTRIB_VALUE_RAW_STRING     = 0x0000000000004000,
public const int DBG_ATTRIB_VALUE_CUSTOM_VIEWER  = 0x0000000000008000,

// Attributes about field access types for the object

public const int DBG_ATTRIB_ACCESS_NONE          = 0x0000000000010000,
public const int DBG_ATTRIB_ACCESS_PUBLIC        = 0x0000000000020000,
public const int DBG_ATTRIB_ACCESS_PRIVATE       = 0x0000000000040000,
public const int DBG_ATTRIB_ACCESS_PROTECTED     = 0x0000000000080000,
public const int DBG_ATTRIB_ACCESS_FINAL         = 0x0000000000100000,
public const int DBG_ATTRIB_ACCESS_ALL           = 0x00000000001f0000,

// Attributes for the storage types of the object

public const int DBG_ATTRIB_STORAGE_NONE         = 0x0000000001000000,
public const int DBG_ATTRIB_STORAGE_GLOBAL       = 0x0000000002000000,
public const int DBG_ATTRIB_STORAGE_STATIC       = 0x0000000004000000,
public const int DBG_ATTRIB_STORAGE_REGISTER     = 0x0000000008000000,
public const int DBG_ATTRIB_STORAGE_ALL          = 0x000000000f000000,

// Attributes for the type modifiers on the object

public const int DBG_ATTRIB_TYPE_NONE            = 0x0000000100000000,
public const int DBG_ATTRIB_TYPE_VIRTUAL         = 0x0000000200000000,
public const int DBG_ATTRIB_TYPE_CONSTANT        = 0x0000000400000000,
public const int DBG_ATTRIB_TYPE_SYNCHRONIZED    = 0x0000000800000000,
public const int DBG_ATTRIB_TYPE_VOLATILE        = 0x0000001000000000,
public const int DBG_ATTRIB_TYPE_ALL             = 0x0000001f00000000,

// Attributes that describe the type of object

public const int DBG_ATTRIB_DATA                 = 0x0000010000000000,
public const int DBG_ATTRIB_METHOD               = 0x0000020000000000,
public const int DBG_ATTRIB_PROPERTY             = 0x0000040000000000,
public const int DBG_ATTRIB_CLASS                = 0x0000080000000000,
public const int DBG_ATTRIB_BASECLASS            = 0x0000100000000000,
public const int DBG_ATTRIB_INTERFACE            = 0x0000200000000000,
public const int DBG_ATTRIB_INNERCLASS           = 0x0000400000000000,
public const int DBG_ATTRIB_MOSTDERIVED          = 0x0000800000000000,
public const int DBG_ATTRIB_CHILD_ALL            = 0x0000ff0000000000,

// Miscellaneous attributes

public const int DBG_ATTRIB_MULTI_CUSTOM_VIEWERS = 0x0001000000000000
```

## <a name="members"></a>成員
 `DBG_ATTRIB_NONE`\
 表示沒有屬性。

 `DBG_ATTRIB_ALL`\
 指出所有屬性。

 `DBG_ATTRIB_OBJ_IS_EXPANDABLE`\
 表示參考或屬性具有子系。

 `DBG_ATTRIB_OBJ_HAS_ID`\
 指出已建立這個物件的識別碼。

 `DBG_ATTRIB_OBJ_CAN_HAVE_ID`\
 表示可以建立這個物件的識別碼。

 `DBG_ATTRIB_VALUE_READONLY`\
 表示值是唯讀值。

 `DBG_ATTRIB_VALUE_ERROR`\
 指出此值為錯誤。

 `DBG_ATTRIB_VALUE_SIDE_EFFECT`\
 指出評估有副作用。

 `DBG_ATTRIB_OVERLOADED_CONTAINER`\
 指出這個屬性實際上是多載的容器。

 `DBG_ATTRIB_VALUE_BOOLEAN`\
 指出中的值 `DEBUG_PROPERTY_INFO::bstrValue` 是布林值。

 `DBG_ATTRIB_VALUE_BOOLEAN_TRUE`\
 指出中的值 `DEBUG_PROPERTY_INFO::bstrValue` 是布林值和 `TRUE` 。

 `DBG_ATTRIB_VALUE_INVALID`\
 表示 `DEBUG_PROPERTY_INFO::bstrValue` 中的值無效。

 `DBG_ATTRIB_VALUE_NAT`\
 指出中的值「 `DEBUG_PROPERTY_INFO::bstrValue` *不是*」 (NAT) 。 NAT 描述 Intel 64 位處理器中的暫存器旗標，指出延遲的推測例外狀況。

 `DBG_ATTRIB_VALUE_AUTOEXPANDED`\
 指出中的值 `DEBUG_PROPERTY_INFO::bstrValue` 可能已自動展開。

 `DBG_ATTRIB_VALUE_TIMEOUT`\
 指出評估已計時。

 `DBG_ATTRIB_VALUE_RAW_STRING`\
 指出中的值 `DEBUG_PROPERTY_INFO::bstrValue` 可以由原始字串表示。

 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER`\
 指出這個屬性至少有一個與其相關聯的自訂檢視器。

 `DBG_ATTRIB_ACCESS_NONE`\
 表示不具有 `public` 、和 `private` 類型存取的物件 `protected` 。

 `DBG_ATTRIB_ACCESS_PUBLIC`\
 表示具有公用存取的物件。

 `DBG_ATTRIB_ACCESS_PRIVATE`\
 表示具有私用存取的物件。

 `DBG_ATTRIB_ACCESS_PROTECTED`\
 表示具有保護存取的物件。

 `DBG_ATTRIB_ACCESS_FINAL`\
 表示具有最終存取的物件。

 `DBG_ATTRIB_ACCESS_ALL`\
 要從中解壓縮存取屬性的遮罩 `DBG_ATTRIB_FLAGS` 。

 `DBG_ATTRIB_STORAGE_NONE`\
 指出未指定任何儲存體類型。

 `DBG_ATTRIB_STORAGE_GLOBAL`\
 表示全域儲存體。

 `DBG_ATTRIB_STORAGE_STATIC`\
 表示靜態儲存體。

 `DBG_ATTRIB_STORAGE_REGISTER`\
 指出註冊中的儲存體。

 `DBG_ATTRIB_STORAGE_ALL`\
 要從中解壓縮儲存體屬性的遮罩 `DBG_ATTRIB_FLAGS` 。

 `DBG_ATTRIB_TYPE_NONE`\
 指出沒有型別修飾詞。

 `DBG_ATTRIB_TYPE_VIRTUAL`\
 指出物件的類型為虛擬。

 `DBG_ATTRIB_TYPE_CONSTANT`\
 表示物件類型是常數。

 `DBG_ATTRIB_TYPE_SYNCHRONIZED`\
 表示物件的類型已同步處理。

 `DBG_ATTRIB_TYPE_VOLATILE`\
 表示物件的類型為 volatile。

 `DBG_ATTRIB_TYPE_ALL`\
 要從中解壓縮型別屬性的遮罩 `DBG_ATTRIB_FLAGS` 。

 `DBG_ATTRIB_DATA`\
 指出此物件是資料欄位。

 `DBG_ATTRIB_METHOD`\
 指出此物件是方法。

 `DBG_ATTRIB_PROPERTY`\
 表示此物件為屬性。

 `DBG_ATTRIB_CLASS`\
 表示此物件為類別。

 `DBG_ATTRIB_BASECLASS`\
 指出此物件是基類。

 `DBG_ATTRIB_INTERFACE`\
 表示此物件為介面。

 `DBG_ATTRIB_INNERCLASS`\
 指出此物件是內部類別。

 `DBG_ATTRIB_MOSTDERIVED`\
 表示此物件為「*最大衍生*」。 「*最大衍生*」一詞是指物件的實際型別，而不是其參考的型別。

 `DBG_ATTRIB_CHILD_ALL`\
 表示的遮罩 `DBG_ATTRIB_DATA` `DBG_ATTRIB_MOSTDERIVED` 。

 `DBG_ATTRIB_MULTI_CUSTOM_VIEWERS`\
 指出物件有多個相關聯的自訂檢視器。

## <a name="remarks"></a>備註

> [!NOTE]
> 此列舉中的值實際上不是在 c # 的元件中定義。 相反地，您必須將定義複製到原始程式檔。

 這些旗標也可用來篩選物件的子系，例如，當做為引數傳遞至 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)時。 這些值可能會與位結合 `OR` 。

 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER`旗標是指 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 從[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)介面取得[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)介面的指示，並呼叫[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)以取得自訂檢視器清單。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
