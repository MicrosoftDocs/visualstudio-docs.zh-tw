---
title: IDebugComPlus符號提供程式2::獲取按名稱獲取類型 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetTypesByName
- IDebugComPlusSymbolProvider2::GetTypesByName
ms.assetid: ef76b1a8-6910-48fe-b4af-d9045eefd23f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5e7b85fb8d5b0e3256e172ff78bc3a5f660b69b8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733427"
---
# <a name="idebugcomplussymbolprovider2gettypesbyname"></a>IDebugComPlusSymbolProvider2::GetTypesByName
檢索給定其名稱的類型。

## <a name="syntax"></a>語法

```cpp
HRESULT GetTypesByName(
    LPCOLESTR          pszClassName,
    NAME_MATCH         nameMatch,
    IEnumDebugFields** ppEnum
);
```

```csharp
int GetTypesByName(
    string               pszClassName,
    enum_ NAME_MATCH     nameMatch,
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>參數
`pszClassName`\
[在]類型的名稱。

`nameMatch`\
[在]選擇匹配類型,例如區分大小寫。 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)枚舉中的值。

`ppEnum`\
[出]包含具有給定名稱的類型或類型的枚舉器。

## <a name="return-value"></a>傳回值
如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
對於泛型類型,要查找「清單\<int>」或\<「清單 int,int>」的名稱將是「清單」。。 如果同名類型出現在多個模組中,則`ppEnum`參數將包含所有副本。 您必須使用[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)`guidModule`並根據 參數進行區分。

## <a name="example"></a>範例
下面的範例展示如何為公開[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)介面的**CDebugSymbol提供程式**物件實現此方法。

```cpp
HRESULT CDebugSymbolProvider::GetTypesByName(
    LPCOLESTR pszClassName,
    NAME_MATCH nameMatch,
    IEnumDebugFields** ppEnum
)
{
    HRESULT hr = S_OK;
    CModIter ModIter;
    CModule* pmodule; // the iterator owns the reference
    CFieldList listField;

    ASSERT(IsValidWideStringPtr(pszClassName));
    ASSERT(IsValidWritePtr(ppEnum, IEnumDebugFields*));

    METHOD_ENTRY( CDebugSymbolProvider::GetTypesByName );

    IfFalseGo( pszClassName && ppEnum, E_INVALIDARG );
    *ppEnum = NULL;

    IfFailGo( GetModuleIter(&ModIter) );

    hr = S_FALSE;

    if ( nameMatch == nmCaseInsensitive)
    {
        while (ModIter.GetNext(&pmodule))
        {
            if (pmodule->FindTypesByNameCaseInsensitive( pszClassName,
                    &listField,
                    this ) )
            {
                hr = S_OK;
            }
        }
    }
    else
    {
        while (ModIter.GetNext(&pmodule))
        {
            if (pmodule->FindTypesByName( pszClassName,
                                          &listField,
                                          this) )
            {
                hr = S_OK;
            }
        }
    }

    // If the list is empty then no type
    IfFalseGo( listField.GetCount(), E_FAIL );

    // Create enumerator
    IfFailGo( CreateEnumerator( ppEnum, &listField ) );

Error:

    METHOD_EXIT( CDebugSymbolProvider::GetTypesByName, hr );

    return hr;
}
```

## <a name="see-also"></a>另請參閱
- [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)
