---
title: IDebugProcessSecurity：： QueryCanSafelyAttach |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa3f2c02610b5fbe99335ccea6d7c566a0fe58df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931457"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
此方法可讓埠供應商在使用者附加至不安全的進程之前顯示警告。

## <a name="syntax"></a>語法

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>傳回值
 傳回值如下所示：

- `S_OK`： [附加至進程] 是安全的，且不會顯示警告對話方塊。

- `S_FALSE`：附加可能是安全性問題，而且會顯示含有警告的對話方塊。

- `FAILURE`：附加至進程失敗。

## <a name="see-also"></a>另請參閱
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
