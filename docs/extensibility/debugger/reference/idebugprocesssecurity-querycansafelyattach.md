---
title: IDebugProcess 安全性::查詢可以安全連接 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e03ccbb7761802401239768c54f4ea5b36ab86bf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723206"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
此方法允許埠供應商在使用者附加到不安全進程之前顯示警告。

## <a name="syntax"></a>語法

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>傳回值
 傳回值的名稱:

- `S_OK`:附加到進程是安全的,並且不顯示警告對話方塊。

- `S_FALSE`:附加可能是一個安全問題,並顯示一個帶有警告的對話方塊。

- `FAILURE`:附加到進程失敗。

## <a name="see-also"></a>另請參閱
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
