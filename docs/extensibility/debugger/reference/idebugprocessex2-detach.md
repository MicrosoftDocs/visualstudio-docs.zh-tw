---
title: IDebugProcessEx2：:D etach |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62ca404442d6bf6080972f03c3e2fd0da2621e20
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954887"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
這個方法會通知進程，會話不再將進程進行偵錯工具。

## <a name="syntax"></a>語法

```cpp
HRESULT Detach( 
   IDebugSession2* pSession
);
```

```csharp
int Detach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>參數
`pSession`\
在值，可唯一識別要卸離此處理程式的會話。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 傳入的介面 `pSession` 只視為 cookie，此值可唯一識別原本附加至此進程的會話 debug manager; 提供的介面上沒有任何方法可正常運作。

## <a name="see-also"></a>另請參閱
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
