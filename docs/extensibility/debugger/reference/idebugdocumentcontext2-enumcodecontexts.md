---
description: 抓取與此檔內容相關聯的所有程式碼內容清單。
title: IDebugDocumentCoNtext2：： EnumCodeCoNtexts |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::EnumCodeContexts
helpviewer_keywords:
- IDebugDocumentContext2::EnumCodeContexts
ms.assetid: 627af69c-5cce-4e1d-8233-5f4d8dbc62e5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d361a0cee6a5c54a11e5497366fe1d82bf30af45
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150597"
---
# <a name="idebugdocumentcontext2enumcodecontexts"></a>IDebugDocumentContext2::EnumCodeContexts
抓取與此檔內容相關聯的所有程式碼內容清單。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumCodeContexts(
    IEnumDebugCodeContexts2** ppEnumCodeCxts
);
```

```csharp
int EnumCodeContexts(
    out IEnumDebugCodeContexts2 ppEnumCodeCxts
);
```

## <a name="parameters"></a>參數
`ppEnumCodeCxts`\

## <a name="return-value"></a>傳回值
如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
當檔使用範本或包含檔案時，單一檔內容可以產生多個程式碼內容。

## <a name="example"></a>範例
下列範例顯示如何針對 `CDebugContext` 公開 [IDebugDocumentCoNtext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 介面的簡單物件，執行這個方法。

```cpp
HRESULT CDebugContext::EnumCodeContexts(IEnumDebugCodeContexts2 **ppEnumCodeCxts)
{
    HRESULT hr;

    // Check for a valid IEnumDebugCodeContexts2 interface pointer.
    if (ppEnumCodeCxts)
    {
        *ppEnumCodeCxts = NULL;

        // Create a CEnumDebugCodeContexts object.
        CComObject<CEnumDebugCodeContexts>* pEnum;
        hr = CComObject<CEnumDebugCodeContexts>::CreateInstance(&pEnum);
        assert(hr == S_OK);
        if (hr == S_OK)
        {
            // Get an IID_IDebugCodeContext2 interface.
            CComPtr<IDebugCodeContext2> spCodeCxt;
            hr = QueryInterface(IID_IDebugCodeContext2,
                                (void**)&spCodeCxt);
            assert(hr == S_OK);
            if (hr == S_OK)
            {
                // Initialize the code context enumerator with the
                // IDebugCodeContext2 information.
                IDebugCodeContext2* rgpCodeContext[] = { spCodeCxt.p };
                hr = pEnum->Init(rgpCodeContext,
                                 &(rgpCodeContext[1]),
                                 NULL,
                                 AtlFlagCopy);
                assert(hr == S_OK);
                if (hr == S_OK)
                {
                // Set the passed IEnumDebugCodeContexts2 pointer equal to the pointer
                // value of the created CEnumDebugCodeContexts object.
                hr = pEnum->QueryInterface(ppEnumCodeCxts);
                assert(hr == S_OK);
                }
            }

            // Otherwise, delete the CEnumDebugCodeContexts object.
            if (FAILED(hr))
            {
                delete pEnum;
            }
        }
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
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
