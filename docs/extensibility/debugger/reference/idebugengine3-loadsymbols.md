---
title: IDebugEngine3::載入符號 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7963d39601a0d3a90ca2daa7632902d7aa506de8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730808"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
此除錯引擎正在除錯的所有模組的載入(根據需要)符號。

## <a name="syntax"></a>語法

```cpp
HRESULT LoadSymbols();
```

```csharp
int LoadSymbols();
```

## <a name="parameters"></a>參數
 無。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則返回錯誤代碼。

## <a name="remarks"></a>備註
 這將載入此除錯引擎引用的所有模組的調試符號。 僅當符號尚未載入時,才會載入這些符號。 符號在調用[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)設置的路徑上搜索。

## <a name="see-also"></a>另請參閱
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
