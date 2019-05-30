---
title: IDebugEngine3::LoadSymbols |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 72c4fce5a7e8dd53093e21db2771d2176462e67c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352515"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
正在偵錯此偵錯引擎的所有模組的載入 （視） 符號。

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
 如果成功，會傳回 S_OK;否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 這會載入此偵錯引擎所參考的所有模組的偵錯符號。 他們尚未載入時，才會載入的符號。 呼叫所設定的路徑上搜尋符號[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)。

## <a name="see-also"></a>另請參閱
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)