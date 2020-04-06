---
title: IDebugProcessEx2::附加 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d70da2530a1677367a22968436a17eba809fd24a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723390"
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
此方法通知進程工作階段正在調試該過程。

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
[在]唯一標識附加到此過程的會話的值。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 傳入的`pSession`介面將僅被視為 Cookie,該值唯一標識附加到此過程的會話調試管理器;提供的介面上沒有任何方法正常工作。

## <a name="see-also"></a>另請參閱
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
