---
title: IDebug文檔上下文2::獲取聲明範圍 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetStatementRange
helpviewer_keywords:
- IDebugDocumentContext2::GetStatementRange
ms.assetid: bc94851a-0ec4-47ea-99c7-0a585e54e726
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50e521d98f10477d56dfece30e20fd000b87b632
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731778"
---
# <a name="idebugdocumentcontext2getstatementrange"></a>IDebugDocumentContext2::GetStatementRange
獲取文檔上下文的檔語句範圍。

## <a name="syntax"></a>語法

```cpp
HRESULT GetStatementRange(
    TEXT_POSITION* pBegPosition,
    TEXT_POSITION* pEndPosition
);
```

```csharp
int GetStatementRange(
    TEXT_POSITION[] pBegPosition,
    TEXT_POSITION[] pEndPosition
);
```

## <a name="parameters"></a>參數
`pBegPosition`\
[進出]用起始位置填充[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)結構。 如果不需要此資訊,則此參數設定為 null 值。

`pEndPosition`\
[進出]用結束位置填充[的TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)結構。 如果不需要此資訊,則此參數設定為 null 值。

## <a name="return-value"></a>傳回值
如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
語句範圍是貢獻本文檔上下文引用的代碼的行的範圍。

要取得本文件上下文中的原始碼(包括註解)範圍,請調用[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)方法。

## <a name="example"></a>範例
下面的範例展示如何為公開[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)`CDebugContext`介面的簡單物件實現此方法。 僅當開始位置不是空值時,此示例才填充結束位置。

```cpp
HRESULT CDebugContext::GetStatementRange(TEXT_POSITION* pBegPosition,
                                         TEXT_POSITION* pEndPosition)
{
    HRESULT hr;

    // Check for a valid beginning position argument pointer.
    if (pBegPosition)
    {
        // Copy the member TEXT_POSITION into the local pBegPosition.
        memcpy(pBegPosition, &m_pos, sizeof (TEXT_POSITION));

        // Check for a valid ending position argument pointer.
        if (pEndPosition)
        {
            // Copy the member TEXT_POSITION into the local pEndPosition.
            memcpy(pEndPosition, &m_pos, sizeof (TEXT_POSITION));
        }
        hr = S_OK;
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>另請參閱
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
