---
title: IDebug參考2::設置價值字串 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsString
helpviewer_keywords:
- IDebugReference2::SetValueAsString
ms.assetid: 9a508ced-fd54-44f5-bb42-ec15c80384d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c8414ce5f53acec2a30ff681ff0bab8ddc919310
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720291"
---
# <a name="idebugreference2setvalueasstring"></a>IDebugReference2::SetValueAsString
設定字串中的引用的值。 保留供未來使用。

## <a name="syntax"></a>語法

```cpp
HRESULT SetValueAsString ( 
   LPCOLESTR pszValue,
   DWORD     dwRadix,
   DWORD     dwTimeout
);
```

```csharp
int SetValueAsString ( 
   string pszValue,
   uint   dwRadix,
   uint   dwTimeout
);
```

## <a name="parameters"></a>參數
`pszValue`\
[在]作為字串的值。

`dwRadix`\
[在]用於格式化任何數值資訊的半徑。

`dwTimeout`\
[在]從此方法返回之前等待的最大時間(以毫秒為單位)。 用於`INFINITE`無限期等待。

## <a name="return-value"></a>傳回值
 永遠會傳回 `E_NOTIMPL`。

## <a name="see-also"></a>另請參閱
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
