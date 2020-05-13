---
title: IDebugModule2::ReloadSymbols_Deprecated |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e776434e17d90cd2c61c926bbf0100a44ecc524b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726926"
---
# <a name="idebugmodule2reloadsymbols_deprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
已過時。 請勿使用。 重新載入此模組的符號。

## <a name="syntax"></a>語法

```cpp
HRESULT ReloadSymbols( 
   LPCOLESTR pszUrlToSymbols,
   BSTR*     pbstrDebugMessage
);
```

```csharp
int ReloadSymbols( 
   string     pszUrlToSymbols,
   out string pbstrDebugMessage
);
```

## <a name="parameters"></a>參數
`pszUrlToSymbols`\
[在]符號存儲的路徑。

`pbstrDebugMessage`\
[出]返回"模組"視窗中顯示在模組名稱右側的資訊性消息,如狀態或錯誤消息。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。 除錯引擎應傳回`E_FAIL`。

## <a name="remarks"></a>備註
 不再支援此方法。 改為實現[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)方法。

## <a name="see-also"></a>另請參閱
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)
