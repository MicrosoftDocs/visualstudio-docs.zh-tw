---
title: IDebug文件上下文2::獲取名稱 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetName
helpviewer_keywords:
- IDebugDocumentContext2::GetName
ms.assetid: 546c5b2e-f166-4edb-9e61-57d797ca98a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 253ef509a60e8bb2ce177235f4b93b370e66f484
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731805"
---
# <a name="idebugdocumentcontext2getname"></a>IDebugDocumentContext2::GetName
獲取包含此文件上下文的文件的可顯示名稱。

## <a name="syntax"></a>語法

```cpp
HRESULT GetName(
    GETNAME_TYPE gnType,
    BSTR*        pbstrFileName
);
```

```csharp
int GetName(
    enum_GETNAME_TYPE  gnType,
    out string         pbstrFileName
);
```

## <a name="parameters"></a>參數
`gnType`\
[在]GETNAME_TYPE[枚舉中](../../../extensibility/debugger/reference/getname-type.md)指定要返回的名稱類型的值。

`pbstrFileName`\
[出]返回檔的名稱。

## <a name="return-value"></a>傳回值
如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
此方法通常將調用轉接到[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)方法,除非編寫文檔上下文以儲存文檔名稱本身(如示例所示)。

## <a name="example"></a>範例
下面的範例展示如何為公開[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)`CDebugContext`介面的簡單物件實現此方法。

```cpp
HRESULT CDebugContext::GetName(GETNAME_TYPE gnType, BSTR* pbstrFileName)
{
    HRESULT hr;

    // Check for a valid file name argument.
    if (pbstrFileName)
    {
        *pbstrFileName = NULL;

        switch (gnType)
        {
            case GN_NAME:
            case GN_FILENAME:
            {
                // Copy the member file name into the local file name.
                *pbstrFileName = SysAllocString(m_sbstrFileName);
                // Check for successful copy.
                hr = (*pbstrFileName) ? S_OK : E_OUTOFMEMORY;
                break;
            }
            default:
            {
                hr = E_FAIL;
                break;
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
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
