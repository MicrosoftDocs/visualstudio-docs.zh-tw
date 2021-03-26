---
description: 判斷會話 debug manager (SDM) 是否可以卸離進程。
title: IDebugProcess2：： CanDetach |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::CanDetach
helpviewer_keywords:
- IDebugProcess2::CanDetach
ms.assetid: 2830f7c3-69fb-474a-97b8-5b869e38d546
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d0ffc6e8ee787960baf7ccb709ab76ab5d66be4d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071684"
---
# <a name="idebugprocess2candetach"></a>IDebugProcess2::CanDetach
判斷會話 debug manager (SDM) 是否可以卸離進程。

## <a name="syntax"></a>語法

```cpp
HRESULT CanDetach(
   void
);
```

```csharp
int CanDetach();
```

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK.` `S_FALSE` 如果偵錯工具無法從進程卸離，則傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
