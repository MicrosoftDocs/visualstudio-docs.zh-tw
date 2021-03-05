---
description: 將這個屬性的值設定為指定之參考的值。
title: IDebugProperty2：： SetValueAsReference |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b5b9529a4e4cd56a2b354eaa7f847db4d9d82be1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166745"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
將這個屬性的值設定為指定之參考的值。

## <a name="syntax"></a>語法

```cpp
HRESULT SetValueAsReference(
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```csharp
int SetValueAsReference(
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

## <a name="parameters"></a>參數
`rgpArgs`\
在要傳遞至 managed 程式碼屬性 setter 的引數陣列。 如果屬性 setter 未採用引數，或此 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 物件未參考這類屬性 setter，則應為 `rgpArgs` null 值。 此參數通常是 null 值。

`dwArgCount`\
在陣列中的引數數目 `rgpArgs` 。

`pValue`\
在以 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 物件形式的參考，指向要用來設定這個屬性的值。

`dwTimeout`\
在設定值所花的時間（以毫秒為單位）。 一般值為 `INFINITE` 。 這會影響任何可能評估所能採用的時間長度。

## <a name="return-value"></a>傳回值
 如果成功，則傳回，否則會傳回 `S_OK` 錯誤碼，通常是下列其中一項：

|錯誤|描述|
|-----------|-----------------|
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|不支援設定參考中的值。|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|因為此屬性參考的是方法，所以無法設定值。|
|`E_SETVALUE_VALUE_IS_READONLY`|此值為唯讀，無法設定。|
|`E_NOTIMPL`|此方法尚未實作。|

## <a name="see-also"></a>另請參閱
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
