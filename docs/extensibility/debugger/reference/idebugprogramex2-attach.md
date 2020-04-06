---
title: IDebugProgramEx2::附加 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fcb52a96074b783043af1e908cf454466df74c30
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722386"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
將會話附加到程式。

## <a name="syntax"></a>語法

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason,
   IDebugSession2*       pSession
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   uint                 dwReason,
   IDebugSession2       pSession
);
```

## <a name="parameters"></a>參數
`pCallback`\
[在][IDebugEvent回調2](../../../extensibility/debugger/reference/idebugeventcallback2.md)物件,表示附加的調試引擎向其發送事件的回調函數。

`dwReason`\
[在]描述附加操作原因[ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)枚舉中的值。

`pSession`\
[在]唯一標識附加到程式的作業階段的值。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則返回錯誤代碼。 如果程式已附加`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`,此方法應返回。

## <a name="remarks"></a>備註
 包含該程式的埠可以使用 中`pSession`的值來確定嘗試附加到該程式的作業階段。 例如,如果埠一次只允許一個調試會話附加到進程,則埠可以確定同一會話是否已附加到進程中的其他程式。

> [!NOTE]
> 傳入的`pSession`介面將僅被視為 Cookie,該值唯一標識附加到此程式的作業階段調試管理器;提供的介面上沒有任何方法正常工作。

## <a name="see-also"></a>另請參閱
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
