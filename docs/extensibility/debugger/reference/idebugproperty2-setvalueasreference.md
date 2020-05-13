---
title: IDebug屬性2::設置價值作為參考 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 73d00ccedc6985061448170735e9ebcaac42f530
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721261"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
將此屬性的值設置為給定引用的值。

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
[在]要傳遞給託管代碼屬性設置器的參數陣列。 如果屬性設定器不採用參數,或者此[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)物件不引用此類屬性設置`rgpArgs`器, 則應為 null 值。 此參數通常是空值。

`dwArgCount`\
[在]陣列中的`rgpArgs`參數數。

`pValue`\
[在]以[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)物件的形式對用於設置此屬性的值的引用。

`dwTimeout`\
[在]設置值需要多長時間(以毫秒為單位)。 典型的值是`INFINITE`。 這會影響任何可能的評估可能需要的時間長度。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則將傳回錯誤代碼,通常為以下代碼之一:

|錯誤|描述|
|-----------|-----------------|
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|不支援從引用中設置值。|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|無法設置該值,因為此屬性引用方法。|
|`E_SETVALUE_VALUE_IS_READONLY`|該值為唯讀,無法設置。|
|`E_NOTIMPL`|此方法尚未實作。|

## <a name="see-also"></a>另請參閱
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
