---
description: 這個方法會通知進程，會話現在正在將進程進行偵錯工具。
title: IDebugProcessEx2：： Attach |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1938ae8299612caabe2fe684b7b5c1af685d4596
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149739"
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
這個方法會通知進程，會話現在正在將進程進行偵錯工具。

## <a name="syntax"></a>語法

```cpp
HRESULT Attach( 
   IDebugSession2* pSession
);
```

```csharp
int Attach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>參數
`pSession`\
在值，可唯一識別附加至此進程的會話。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 傳入的介面只會被 `pSession` 視為 cookie，此值可唯一識別附加至此進程的會話 debug manager。提供的介面上沒有任何方法可正常運作。

## <a name="see-also"></a>另請參閱
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
