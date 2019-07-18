---
title: IDebugProcessSecurity::QueryCanSafelyAttach |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec541b6dc4ccae57628d4b33e7c188008da6edae
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187958"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
這個方法可讓使用者附加至不安全的程序之前，顯示警告的連接埠提供者。

## <a name="syntax"></a>語法

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>傳回值
 傳回的值如下所示：

- `S_OK`：附加至處理序是安全且沒有警告 對話方塊中會顯示。

- `S_FALSE`：附加可能有安全性問題，但有警告的對話方塊隨即顯示。

- `FAILURE`：附加至處理序就會失敗。

## <a name="see-also"></a>另請參閱
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)