---
title: IDebugModule2：： ReloadSymbols_Deprecated |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7d4e484a1557ea99138f31fdc6f9103e6708b803
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929748"
---
# <a name="idebugmodule2reloadsymbols_deprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
已過時。 請勿使用。 重載此模組的符號。

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
在符號存放區的路徑。

`pbstrDebugMessage`\
擴展傳回在 [模組] 視窗中，顯示于模組名稱右邊的參考訊息，例如狀態或錯誤訊息。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。 調試引擎應該一律傳回 `E_FAIL` 。

## <a name="remarks"></a>備註
 不再支援此方法。 請改為執行 [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) 方法。

## <a name="see-also"></a>另請參閱
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)
