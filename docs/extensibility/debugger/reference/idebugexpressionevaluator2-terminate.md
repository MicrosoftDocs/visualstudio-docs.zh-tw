---
title: IDebug運算式賦值器2::終止 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Terminate
- IDebugExpressionEvaluator2::Terminate
ms.assetid: 38265100-4d80-4902-833a-07bb569f9ba8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5460930cbcc528648c2a6c502ef7eb9acbe00d62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729151"
---
# <a name="idebugexpressionevaluator2terminate"></a>IDebugExpressionEvaluator2::Terminate
停止並清理表達式賦值器。

## <a name="syntax"></a>語法

```cpp
HRESULT Terminate (
    void
);
```

```csharp
int Terminate ();
```

## <a name="return-value"></a>傳回值
如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
清理表達式賦值器時告訴該表達式賦值器。

## <a name="example"></a>範例
下面的範例展示如何為公開[IDebugExpression評估器2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)介面的**運算式計算機包**物件實現此方法。

```cpp
STDMETHODIMP ExpressionEvaluatorPackage::Terminate(void)
{
    // scan the namespaces contained and delete
    EEExtensionMethodCache **ppChild = NULL;
    m_HashExtensionMethodCache.ResetHashIterator();
    while (ppChild = m_HashExtensionMethodCache.IterateHash())
    {
        delete *ppChild;
    }
    return VBEEImplicitVariables::Terminate();
}
```

## <a name="see-also"></a>另請參閱
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
