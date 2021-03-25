---
description: 將會話附加至程式。
title: IDebugProgramEx2：： Attach |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f4f7f6a083c37ece73be488ab0c4f6d4c25ce24c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084151"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
將會話附加至程式。

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
在 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 物件，表示附加的 debug engine 將事件傳送至其中的回呼函數。

`dwReason`\
在 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) 列舉中的值，這個值會描述附加作業的原因。

`pSession`\
在值，可唯一識別附加至程式的會話。

## <a name="return-value"></a>傳回值
 如果成功，則傳回，否則會傳回 `S_OK` 錯誤碼。 如果已附加程式，則此方法應該會傳回 `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` 。

## <a name="remarks"></a>備註
 包含程式的埠可以使用中的值 `pSession` ，來判斷哪一個會話正在嘗試附加至程式。 例如，如果埠一次只允許一個 debug 會話附加至進程，則埠可以判斷是否已將相同的會話附加至進程中的其他程式。

> [!NOTE]
> 傳入的介面只會被 `pSession` 視為 cookie，此值可唯一識別附加至此程式的會話 debug manager; 提供的介面上沒有任何方法可正常運作。

## <a name="see-also"></a>另請參閱
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
