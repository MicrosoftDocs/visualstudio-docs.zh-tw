---
title: IDebugDocumentContext2::GetStatementRange |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2::GetStatementRange
helpviewer_keywords:
- IDebugDocumentContext2::GetStatementRange
ms.assetid: bc94851a-0ec4-47ea-99c7-0a585e54e726
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0707b241b52c1ea9c587970f3a3eb4ae097716c3
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2019
ms.locfileid: "56450239"
---
# <a name="idebugdocumentcontext2getstatementrange"></a>IDebugDocumentContext2::GetStatementRange
取得檔案陳述式的範圍的文件內容。

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

#### <a name="parameters"></a>參數
`pBegPosition`  
[in、 out]A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)會填入的開始位置的結構。 如果不需要這項資訊，請將這個引數為 null 值。

`pEndPosition`  
[in、 out]A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)會填入結束位置的結構。 如果不需要這項資訊，請將這個引數為 null 值。

## <a name="return-value"></a>傳回值
如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
陳述式的範圍是提供此文件內容所參考的程式碼行的範圍。

若要取得此文件內容中的各種來源 （包括註解） 的程式碼，呼叫[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)方法。

## <a name="example"></a>範例
下列範例示範如何實作這個方法來簡單`CDebugContext`公開的物件[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)介面。 此範例中會填入結束的位置只有開頭位置不是 null 值。

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
[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)  
[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)  
[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
