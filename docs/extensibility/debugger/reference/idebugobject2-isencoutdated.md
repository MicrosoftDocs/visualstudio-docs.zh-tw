---
title: IDebugObject2::Isc過時 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a90ff97b87ec2abaab87dfece5b2a2ac1cabb28c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726097"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
此方法確定此物件或父容器的編輯並繼續狀態是否已過期。 自定義表示式賦值器不實現此方法,並且始終返回`E_NOTIMPL`。

## <a name="syntax"></a>語法

```cpp
HRESULT IsEncOutdated(
   BOOL* pfEncOutdated
);
```

```csharp
int IsEncOutdated(
   out int pfEncOutdated
);
```

## <a name="parameters"></a>參數
`pfEncOutdated`\
[出]如果"編輯`TRUE`"和"繼續"狀態已過期,則非零`FALSE`( ) 如果不是。"

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

> [!NOTE]
> 自訂表示式賦值器應始終返回`E_NOTIMPL`。

## <a name="see-also"></a>另請參閱
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
