---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Microsoft Docs
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
ms.openlocfilehash: 44b125f44f3345e7bd28a9993a7a44be2e378b53
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56701429"
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

-   `S_OK`：附加至處理序是安全且沒有警告 對話方塊中會顯示。

-   `S_FALSE`：附加可能有安全性問題，但有警告的對話方塊隨即顯示。

-   `FAILURE`：附加至處理序就會失敗。

## <a name="see-also"></a>另請參閱
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)