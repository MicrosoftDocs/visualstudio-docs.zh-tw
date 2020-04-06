---
title: IDebugEngine3::設置符號路徑 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fbe5128900fa10147c747cbcba4129e96d4c4ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730670"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
設置搜索調試符號的路徑或路徑。

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
[在]包含符號搜尋路徑或路徑的字串。 有關詳細資訊,請參閱"備註"。 不可為 null。

`szSymbolCachePath`\
[在]包含可以快取符號的本地路徑的字串。 不可為 null。

`Flags`\
[在]未使用;始終設置為 0。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則返回錯誤代碼。

## <a name="remarks"></a>備註
 該字串`szSymbolSearchPath`是一個或多個路徑的清單,由分號分隔,以搜索符號。 這些路徑可以是本地路徑、UNC 樣式路徑或 URL。 這些路徑也可以是不同類型的混合路徑。 如果路徑為 UNC(例如,[Symserver]Symbols),\\則調試引擎應確定路徑是否屬於符號伺服器,並且應該能夠從該伺服器載入符號,將其緩存在`szSymbolCachePath`指定的 路徑中。

 符號路徑還可以包含一個或多個緩存位置。 快取按優先順序順序順序出,優先快取優先,並由 *符號分隔。 例如：

```
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com
```

 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)方法執行符號的實際負載。

## <a name="see-also"></a>另請參閱
- [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
