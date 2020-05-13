---
title: IEnum調試欄位:重置 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Reset
helpviewer_keywords:
- IEnumDebugFields::Reset method
ms.assetid: 38ff61e4-0120-42e8-971a-16be6050b425
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: be33249ef583776f613c6716143249e3ce31bc8d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716861"
---
# <a name="ienumdebugfieldsreset"></a>IEnumDebugFields::Reset
此方法將枚舉重置為第一個元素。

## <a name="syntax"></a>語法

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

#### <a name="parameters"></a>參數
 None

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 調用此方法後,下一個調用[Next](../../../extensibility/debugger/reference/ienumdebugfields-next.md)將返回枚舉的第一個元素。

## <a name="see-also"></a>另請參閱
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [下一步](../../../extensibility/debugger/reference/ienumdebugfields-next.md)
