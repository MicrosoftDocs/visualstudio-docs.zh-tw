---
description: 設定要搜尋的路徑或路徑以進行偵錯工具符號。
title: IDebugEngine3：： SetSymbolPath |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e2b029413e3b402e1d8dfa19ccb3ad22644b241
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153686"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
設定要搜尋的路徑或路徑以進行偵錯工具符號。

## <a name="syntax"></a>語法

```cpp
HRESULT SetSymbolPath (
   LPOLESTR            szSymbolSearchPath,
   LPOLESTR            szSymbolCachePath,
   LOAD_SYMBOLS_FLAGS  Flags
);
```

```csharp
int SetSymbolPath(
   string                    szSymbolSearchPath,
   string                    szSymbolCachePath,
   enum_LOAD_SYMBOLS_FLAGS   Flags
);
```

## <a name="parameters"></a>參數

`szSymbolSearchPath`\
在包含符號搜尋路徑或路徑的字串。 如需詳細資訊，請參閱「備註」。 不可以是 null。

`szSymbolCachePath`\
在字串，包含可快取符號的本機路徑。 不可以是 null。

`Flags`\
在未使用;一律設定為0。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 字串 `szSymbolSearchPath` 是一個或多個以分號分隔的路徑清單，以搜尋符號。 這些路徑可以是本機路徑、UNC 樣式的路徑或 URL。 這些路徑也可以混合不同的類型。 如果路徑是 UNC (例如， \\ \Symserver\Symbols) ，則 debug engine 應判斷路徑是否為符號伺服器，而且應該能夠從該伺服器載入符號，並將它們快取在指定的路徑中 `szSymbolCachePath` 。

 符號路徑也可以包含一或多個快取位置。 快取會依優先順序列出，最高優先順序快取優先，並以 * 符號分隔。 例如：

```
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com
```

 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)方法會執行符號的實際載入。

## <a name="see-also"></a>另請參閱
- [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
