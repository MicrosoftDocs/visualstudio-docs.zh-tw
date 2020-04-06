---
title: DBG_ATTRIB_FLAGS |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DBG_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS enumerations
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1c8b3f52eff80c187d3c43b87cea804ace483169
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737553"
---
# <a name="dbg_attrib_flags"></a>DBG_ATTRIB_FLAGS
描述[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)或[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)介面的各種屬性。 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構的成員。

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
 指示所有屬性。

 `DBG_ATTRIB_OBJ_IS_EXPANDABLE`\
 表示參考或屬性具有子系。

 `DBG_ATTRIB_OBJ_HAS_ID`\
 指示已創建此物件的 ID。

 `DBG_ATTRIB_OBJ_CAN_HAVE_ID`\
 指示可以為此物件創建 ID。

 `DBG_ATTRIB_VALUE_READONLY`\
 表示值是唯讀值。

 `DBG_ATTRIB_VALUE_ERROR`\
 指示該值是錯誤。

 `DBG_ATTRIB_VALUE_SIDE_EFFECT`\
 表示評估有副作用。

 `DBG_ATTRIB_OVERLOADED_CONTAINER`\
 指示此屬性實際上是一個重載的容器。

 `DBG_ATTRIB_VALUE_BOOLEAN`\
 指示`DEBUG_PROPERTY_INFO::bstrValue`中的值為布爾。

 `DBG_ATTRIB_VALUE_BOOLEAN_TRUE`\
 指示的`DEBUG_PROPERTY_INFO::bstrValue`值為布林`TRUE`和 。

 `DBG_ATTRIB_VALUE_INVALID`\
 表示 `DEBUG_PROPERTY_INFO::bstrValue` 中的值無效。

 `DBG_ATTRIB_VALUE_NAT`\
 指示`DEBUG_PROPERTY_INFO::bstrValue`中 的值是「*不是事物*」(NAT)。 NAT 描述了英特爾 64 位元處理器中的寄存器標誌,指示延遲的推測異常。

 `DBG_ATTRIB_VALUE_AUTOEXPANDED`\
 指示`DEBUG_PROPERTY_INFO::bstrValue`中的值可能已自動展開。

 `DBG_ATTRIB_VALUE_TIMEOUT`\
 指示評估已超時。

 `DBG_ATTRIB_VALUE_RAW_STRING`\
 指示`DEBUG_PROPERTY_INFO::bstrValue`中的值可以由原始字串表示。

 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER`\
 指示此屬性至少有一個與之關聯的自定義查看器。

 `DBG_ATTRIB_ACCESS_NONE`\
 指示既沒有`public``private`、`protected`也沒有類型存取的物件。

 `DBG_ATTRIB_ACCESS_PUBLIC`\
 表示具有公用存取的物件。

 `DBG_ATTRIB_ACCESS_PRIVATE`\
 表示具有私用存取的物件。

 `DBG_ATTRIB_ACCESS_PROTECTED`\
 表示具有保護存取的物件。

 `DBG_ATTRIB_ACCESS_FINAL`\
 表示具有最終存取的物件。

 `DBG_ATTRIB_ACCESS_ALL`\
 從 中提取訪問屬性`DBG_ATTRIB_FLAGS`的 掩碼。

 `DBG_ATTRIB_STORAGE_NONE`\
 指示未指定存儲類型。

 `DBG_ATTRIB_STORAGE_GLOBAL`\
 表示全域儲存體。

 `DBG_ATTRIB_STORAGE_STATIC`\
 表示靜態儲存體。

 `DBG_ATTRIB_STORAGE_REGISTER`\
 指示寄存器中的存儲。

 `DBG_ATTRIB_STORAGE_ALL`\
 從中提取存儲屬性的掩`DBG_ATTRIB_FLAGS`碼。

 `DBG_ATTRIB_TYPE_NONE`\
 指示沒有類型修改器。

 `DBG_ATTRIB_TYPE_VIRTUAL`\
 指示物件的類型為虛擬物件。

 `DBG_ATTRIB_TYPE_CONSTANT`\
 表示物件類型是常數。

 `DBG_ATTRIB_TYPE_SYNCHRONIZED`\
 指示物件的類型是同步的。

 `DBG_ATTRIB_TYPE_VOLATILE`\
 指示對象的類型是可變的。

 `DBG_ATTRIB_TYPE_ALL`\
 從 中提取類型屬性的`DBG_ATTRIB_FLAGS`掩碼。

 `DBG_ATTRIB_DATA`\
 指示此對象是數據欄位。

 `DBG_ATTRIB_METHOD`\
 指示此對像是方法。

 `DBG_ATTRIB_PROPERTY`\
 指示此對像是屬性。

 `DBG_ATTRIB_CLASS`\
 指示此對像是類。

 `DBG_ATTRIB_BASECLASS`\
 指示此對像是基類。

 `DBG_ATTRIB_INTERFACE`\
 指示此對像是介面。

 `DBG_ATTRIB_INNERCLASS`\
 指示此對像是內部類。

 `DBG_ATTRIB_MOSTDERIVED`\
 指示此物件是「*最派生的*」。 術語"*最派生*「是指物件的實際類型,而不是其引用的類型。

 `DBG_ATTRIB_CHILD_ALL`\
 指示`DBG_ATTRIB_DATA`的遮罩`DBG_ATTRIB_MOSTDERIVED`。

 `DBG_ATTRIB_MULTI_CUSTOM_VIEWERS`\
 指示物件有多個與其關聯的自定義查看器。

## <a name="remarks"></a>備註

> [!NOTE]
> 此枚舉中的值實際上未在 C# 的程式集中定義。 相反,必須將定義複製到源檔。

 這些標誌還用於篩選物件的子級,例如,當作為參數傳遞給[Enum 兒童](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)時。 這些值可以稍微結合`OR`。

 該`DBG_ATTRIB_VALUE_CUSTOM_VIEWER`標誌是[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]從[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)介面獲取[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)介面並調用[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)以獲取自訂檢視器清單的指示。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
