---
description: 這個方法會將列舉欄位重設為第一個元素。
title: IEnumDebugFields：： Reset |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Reset
helpviewer_keywords:
- IEnumDebugFields::Reset method
ms.assetid: 38ff61e4-0120-42e8-971a-16be6050b425
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fedc24c3f51a2a4cbdfae9464f13791f9d8ec1d1
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102226601"
---
# <a name="ienumdebugfieldsreset"></a>IEnumDebugFields::Reset
這個方法會將列舉重設為第一個元素。

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
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 呼叫這個方法之後， [下一次](../../../extensibility/debugger/reference/ienumdebugfields-next.md) 呼叫會傳回列舉的第一個元素。

## <a name="see-also"></a>另請參閱
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [下一步](../../../extensibility/debugger/reference/ienumdebugfields-next.md)
