---
title: IDebug參考2::枚舉兒童 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::EnumChildren
helpviewer_keywords:
- IDebugReference2::EnumChildren
ms.assetid: 35b3c2f3-69f4-4013-b555-f847221f62e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 96b2fec782ce88dfb2200df35f56b35b304beda5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720628"
---
# <a name="idebugreference2enumchildren"></a>IDebugReference2::EnumChildren
取得選取的引言子級的清單。 保留供未來使用。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumChildren ( 
   DEBUGREF_INFO_FLAGS        dwFields,
   DWORD                      dwRadix,
   DBG_ATTRIB_FLAGS           dwAttribFilter,
   LPCOLESTR                  pszNameFilter,
   DWORD                      dwTimeout,
   IEnumDebugReferenceInfo2** ppEnum
);
```

```csharp
int EnumChildren ( 
   enum_DEBUGREF_INFO_FLAGS     dwFields,
   uint                         dwRadix,
   enum_DBG_ATTRIB_FLAGS        dwAttribFilter,
   string                       pszNameFilter,
   uint                         dwTimeout,
   out IEnumDebugReferenceInfo2 ppEnum
);
```

## <a name="parameters"></a>參數
`dwFields`\
[在][DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)枚舉中的標誌的組合,指定要填充枚舉[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)結構中的欄位。

`dwRadix`\
[在]用於格式化任何數值資訊的半徑。

`dwAttribFilter`\
[在][DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)枚舉中的標誌`pszNameFilter`與 參數結合使用,以選擇要枚舉的結構的組合。

`pszNameFilter`\
[在]指定篩選器的字串,如"MyX",與`dwAttribFilter`參數結合使用,用於選擇要枚舉的結構。

`dwTimeout`\
[在]從此方法返回之前等待的最大時間(以毫秒為單位)。 用於`INFINITE`無限期等待。

`ppEnum`\
[出]返回包含請求子屬性清單的[IEnumDebugReference Info2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)物件。

## <a name="return-value"></a>傳回值
 永遠會傳回 `E_NOTIMPL`。

## <a name="see-also"></a>另請參閱
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
