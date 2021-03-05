---
description: 判斷物件是否代表使用者資料。
title: IDebugObject2：： IsUserData |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b9264ed546a4f1c9abcf42b1376e0b21b0f27940
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169985"
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
判斷物件是否代表使用者資料。

## <a name="syntax"></a>語法

```cpp
HRESULT IsUserData(
   BOOL* pfUser
);
```

```csharp
int IsUserData(
   out int pfUser
);
```

## <a name="parameters"></a>參數
`pfUser`\
擴展 `TRUE` 如果物件代表使用者資料，則傳回非零的 () ; 如果不是，則傳回零 (`FALSE`) 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 使用者資料是屬於指定為 JustMyCode 之模組一部分的任何物件 (可設定的選項，可將模組標記為使用者程式碼，因此可在堆疊追蹤) 中看到。

## <a name="see-also"></a>另請參閱
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
