---
title: IDebugObject2：： IsUserData |Microsoft Docs
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
ms.openlocfilehash: 1c53281ee144d3a1fa771fe4e77bba6bb418356e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953353"
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
