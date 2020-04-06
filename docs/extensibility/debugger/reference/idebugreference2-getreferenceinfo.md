---
title: IDebug參考2::獲取參考資訊 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetReferenceInfo
helpviewer_keywords:
- IDebugReference2::GetReferenceInfo
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4fa198a3ded56a0dd054cf225bfb6b10968d1da3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720416"
---
# <a name="idebugreference2getreferenceinfo"></a>IDebugReference2::GetReferenceInfo
獲取描述引用[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)結構。 保留供未來使用。

## <a name="syntax"></a>語法

```cpp
HRESULT GetReferenceInfo ( 
   DEBUGREF_INFO_FLAGS   dwFields,
   DWORD                 nRadix,
   DWORD                 dwTimeout,
   IDebugReference2**    rgpArgs,
   DWORD                 dwArgCount,
   DEBUG_REFERENCE_INFO* pReferenceInfo
);
```

```csharp
int GetReferenceInfo ( 
   enum_DEBUGREF_INFO_FLAGS  dwFields,
   uint                      nRadix,
   uint                      dwTimeout,
   IDebugReference2[]        rgpArgs,
   uint                      dwArgCount,
   DEBUG_REFERENCE_INFO[]    pReferenceInfo
);
```

## <a name="parameters"></a>參數
`dwFields`\
[在]DEBUGREF_INFO_FLAGS[枚舉](../../../extensibility/debugger/reference/debugref-info-flags.md)中的標誌的組合,用於確定要在[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)結構中填寫的欄位。

`nRadix`\
[在]用於格式化任何數值資訊的半徑。

`dwTimeout`\
[在]從此方法返回之前等待的最大時間(以毫秒為單位)。 用於`INFINITE`無限期等待。

`rgpArgs`\
[在][IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)物件的陣列。 保留供將來使用;設置為空值。

`dwArgCount`\
[在]陣列中的`rgpArgs`引為參數數。 保留供將來使用;設置為 0。

`pReferenceInfo`\
[出]一[個DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)結構,該結構填充了屬性的說明。

## <a name="return-value"></a>傳回值
 永遠會傳回 `E_NOTIMPL`。

## <a name="see-also"></a>另請參閱
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
