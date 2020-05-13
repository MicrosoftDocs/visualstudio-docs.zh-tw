---
title: IDebugModule3::載入符號 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c61339305200acc9a6c572a1a96595dc4cb6f50
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726783"
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
載入目前的模組的符號。

## <a name="syntax"></a>語法

```cpp
HRESULT LoadSymbols(
   void
);
```

```csharp
int LoadSymbols();
```

## <a name="return-value"></a>傳回值
 如果方法成功，它會傳回 `S_OK`。 如果方法失敗，則會傳回錯誤碼。

## <a name="remarks"></a>備註
 此方法從當前搜索路徑載入符號(可以通過調用[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)方法來更改)。

 此方法優先於[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)方法。

## <a name="see-also"></a>另請參閱
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
