---
title: IDebugStackFrame2::枚舉屬性 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::EnumProperties
helpviewer_keywords:
- IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f822f20cf4fb7a6fd5aa71b9cc1ec26bcd90e234
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719907"
---
# <a name="idebugstackframe2enumproperties"></a>IDebugStackFrame2::EnumProperties
為與堆疊框架關聯的屬性(如局部變數)創建枚舉器。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumProperties ( 
   DEBUGPROP_INFO_FLAGS      dwFieldSpec,
   UINT                      nRadix,
   REFIID                    refiid,
   DWORD                     dwTimeout,
   ULONG*                    pcelt,
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int EnumProperties ( 
   enum_DEBUGPROP_INFO_FLAGS   dwFieldSpec,
   uint                        nRadix,
   ref Guid                    refiid,
   uint                        dwTimeout,
   out uint                    pcelt,
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>參數
`dwFieldSpec`\
[在][DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)枚舉中的標誌的組合,指定要填充枚舉[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構中的欄位。

`nRadix`\
[在]用於格式化任何數值資訊的半徑。

`refiid`\
[在]選擇要枚[舉DEBUG_PROPERTY_INFO結構](../../../extensibility/debugger/reference/debug-property-info.md)的篩選器的 GUID,例如`guidFilterLocals`。

`dwTimeout`\
[在]從此方法返回之前等待的最大時間(以毫秒為單位)。 用於`INFINITE`無限期等待。

`pcelt`\
[出]返回枚舉的屬性數。 這與調用[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)方法相同。

`ppEnum`\
[出]返回包含所需屬性清單的[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 由於此方法允許使用單個調用檢索所有選定的屬性,因此比按順序調用[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)和[Enum 兒童](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)方法要快。

## <a name="see-also"></a>另請參閱
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)
- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
