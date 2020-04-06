---
title: IDebug屬性2::枚舉兒童 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d6d3908c469b489eb16e4662f7515ea624825e3b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721518"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
檢索屬性的子項清單。

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
[在][DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)枚舉中的標誌的組合,指定要填充枚舉[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構中的欄位。

`dwRadix`\
[在]指定用於格式化任何數值資訊的半徑。

`guidFilter`\
[在]與`dwAttribFilter``pszNameFilter`和 參數一起使用的篩選器的`DEBUG_PROPERTY_INFO`GUID, 用於選擇要枚舉的子級。 例如,`guidFilterLocals`局部變數的篩選器。

`dwAttribFilter`\
[在][DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)枚舉中的標誌的組合,用於指定要枚舉的物件類型,`DBG_ATTRIB_METHOD`例如,對於可能是此屬性子級的所有方法。 與`guidFilter``pszNameFilter`和參數結合使用。

`pszNameFilter`\
[在]與`guidFilter``dwAttribFilter`參數一起使用的篩選器的名稱,用於選擇要枚`DEBUG_PROPERTY_INFO`舉的子級。 例如,為所有名為"MyX"的子級設置此參數為"MyX"篩選器。

`dwTimeout`\
[在]指定從此方法返回之前等待的最大時間(以毫秒為單位)。 用於`INFINITE`無限期等待。

`ppEnum`\
[出]返回包含子屬性清單的[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則返回錯誤代碼。

## <a name="see-also"></a>另請參閱
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
