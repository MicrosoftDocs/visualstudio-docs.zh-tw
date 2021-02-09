---
title: IDebugProcess2：： CanDetach |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::CanDetach
helpviewer_keywords:
- IDebugProcess2::CanDetach
ms.assetid: 2830f7c3-69fb-474a-97b8-5b869e38d546
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 06cad6406951467339d34e467c6de3677cda724a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874161"
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
