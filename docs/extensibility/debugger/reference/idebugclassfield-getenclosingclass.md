---
description: 取得括住這個類別的類別。
title: IDebugClassField：： GetEnclosingClass |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c59eb2559634c67b210f4fc3b4ce41743346c8ea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088480"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
取得括住這個類別的類別。

## <a name="syntax"></a>語法

```cpp
HRESULT GetEnclosingClass(
    IDebugClassField** ppClassField
);
```

```csharp
int GetEnclosingClass(
    out IDebugClassField ppClassField
);
```

## <a name="parameters"></a>參數
`ppClassField`\
擴展傳回代表封閉類別的 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) 物件。 如果沒有封入類別，則會傳回 null 值。

## <a name="return-value"></a>傳回值
如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
如果這個 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) 物件所代表的類別是嵌套類別，則參數會傳回 `ppClassField` 代表封入 `IDebugClassField` 類別的物件。 例如，假設有這個類別定義：

```
class RootClass {
    class NestedClass { }
};
```

`GetEnclosingClass`在代表類別的物件上呼叫方法，會傳回 `IDebugClassField` `NestedClass` `IDebugClassField` 代表類別的物件 `RootClass` 。

## <a name="see-also"></a>另請參閱
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
