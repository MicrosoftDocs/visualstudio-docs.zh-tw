---
title: IDebugClassField::GetEnclosingClass |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6927a63241e2f2794fb5c70945962e00a1676431
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329504"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
取得包含這個類別的類別。

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
[out]傳回[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)物件，表示封入類別。 如果沒有封入類別，則傳回 null 值。

## <a name="return-value"></a>傳回值
如果成功，會傳回 S_OK;否則，傳回錯誤碼。

## <a name="remarks"></a>備註
如果類別以表示這[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)物件是巢狀的類別，則`ppClassField`參數會傳回`IDebugClassField`物件，表示封入類別。 例如，假設此類別定義：

```
class RootClass {
    class NestedClass { }
};
```

呼叫`GetEnclosingClass`方法`IDebugClassField`物件，代表`NestedClass`類別會傳回`IDebugClassField`物件，表示類別`RootClass`。

## <a name="see-also"></a>另請參閱
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
