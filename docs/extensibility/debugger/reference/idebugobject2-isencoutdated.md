---
description: 這個方法會判斷這個物件或父容器的 [編輯後繼續] 狀態是否已過期。
title: IDebugObject2：： IsEncOutdated |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e9b78eb0295d039d4f5d8ca3169cb77d04321aaf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053733"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
這個方法會判斷這個物件或父容器的 [編輯後繼續] 狀態是否已過期。 自訂表格達式評估工具不會執行這個方法，且一律會傳回 `E_NOTIMPL` 。

## <a name="syntax"></a>語法

```cpp
HRESULT IsEncOutdated(
   BOOL* pfEncOutdated
);
```

```csharp
int IsEncOutdated(
   out int pfEncOutdated
);
```

## <a name="parameters"></a>參數
`pfEncOutdated`\
擴展非零 (`TRUE`) 如果 [編輯後繼續] 狀態為 [已過期]，則零 (`FALSE`) （如果沒有的話）。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

> [!NOTE]
> 自訂表格達式評估工具應該一律傳回 `E_NOTIMPL` 。

## <a name="see-also"></a>另請參閱
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
