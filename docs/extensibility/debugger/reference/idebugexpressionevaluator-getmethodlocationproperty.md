---
title: IDebug運算式評估器::獲取方法定位屬性 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6ba87d6c1a1f7370ce5e209440589f362b87035
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729515"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
此方法將方法位置和偏移轉換為記憶體位址。

## <a name="syntax"></a>語法

```cpp
HRESULT GetMethodLocationProperty( 
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   IDebugProperty2**     ppProperty
);
```

```csharp
int GetMethodLocationProperty(
   string               upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   out IDebugProperty2  ppProperty
);
```

## <a name="parameters"></a>參數
`upstrFullyQualifiedMethodPlusOffset`\
[在]方法位置和偏移,表示為字串。

`pSymbolProvider`\
[在]符號提供程式表示為[IDebugSymbol 提供程式](../../../extensibility/debugger/reference/idebugsymbolprovider.md)物件。

`pAddress`\
[在]方法中的位址,表示為[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)物件。

`pBinder`\
[在]活頁夾表示為[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)物件。

`ppProperty`\
[出]返回表示記憶體位址的[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)介面。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 例如,返回的位址可用於設置斷點。

 儘管名稱`upstrFullyQualifiedMethodPlusOffset`,此參數可以傳遞一個部分限定的方法名稱。 在這種情況下,所選方法是包含的方法`pAddress`。 如何解釋此參數由表達式賦值器及其支援的語言的實現決定。

## <a name="see-also"></a>另請參閱
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
