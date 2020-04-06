---
title: IDebugClassField:獲取封閉類 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e5a68e32da370d6881eb2b74cbca157f7b899329
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734402"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
獲取包含此類的類。

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
[出]返回表示封閉類的[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)物件。 如果沒有封閉類,則返回 null 值。

## <a name="return-value"></a>傳回值
如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
如果此[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)物件表示的類是嵌套類`ppClassField`,則 參數將`IDebugClassField`返回表示封閉 類的物件。 例如,給定此類定義:

```
class RootClass {
    class NestedClass { }
};
```

在表示`GetEnclosingClass``IDebugClassField``NestedClass`類的物件上調用 方法返回`IDebugClassField``RootClass`表示類 的物件。

## <a name="see-also"></a>另請參閱
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
