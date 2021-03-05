---
description: 抓取屬性的子系列表。
title: IDebugProperty2：： EnumChildren |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7c9cade8cb0468c78ba03e2beec682d7c2284be0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166953"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
抓取屬性的子系列表。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumChildren ( 
   DEBUGPROP_INFO_FLAGS      dwFields,
   DWORD                     dwRadix,
   REFGUID                   guidFilter,
   DBG_ATTRIB_FLAGS          dwAttribFilter,
   LPCOLESTR                 pszNameFilter,
   DWORD                     dwTimeout,
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int EnumChildren ( 
   enum_DEBUGPROP_INFO_FLAGS   dwFields,
   uint                        dwRadix,
   ref Guid                    guidFilter,
   uint                        dwAttribFilter,
   string                      pszNameFilter,
   uint                        dwTimeout,
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>參數
`dwFields`\
在 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) 列舉中的旗標組合，可指定要填入列舉 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 結構中的哪些欄位。

`dwRadix`\
在指定格式化任何數值資訊時要使用的基數。

`guidFilter`\
在搭配和參數使用之篩選準則的 GUID， `dwAttribFilter` `pszNameFilter` 以選取 `DEBUG_PROPERTY_INFO` 要列舉的子系。 例如， `guidFilterLocals` 篩選本機變數。

`dwAttribFilter`\
在 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) 列舉中的旗標組合，可指定要列舉的物件類型，例如， `DBG_ATTRIB_METHOD` 可能是這個屬性之子系的所有方法。 搭配和參數一起使用 `guidFilter` `pszNameFilter` 。

`pszNameFilter`\
在搭配和參數使用的篩選名稱， `guidFilter` `dwAttribFilter` 可選取 `DEBUG_PROPERTY_INFO` 要列舉的子系。 例如，將此參數設定為 "MyX"，以篩選名稱為 "MyX" 的所有子系。

`dwTimeout`\
在指定從這個方法傳回之前等候的最長時間（以毫秒為單位）。 使用 `INFINITE` 可無限期等候。

`ppEnum`\
擴展傳回 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) 物件，其中包含子屬性的清單。

## <a name="return-value"></a>傳回值
 如果成功，則傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
