---
description: 傳回指定之標記的中繼資料物件所關聯的名稱。
title: IDebugComPlusSymbolProvider：： GetNameFromToken |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetNameFromToken
- GetNameFromToken
ms.assetid: 6e8cf468-5fd1-4655-93ed-88828d6068b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04501860ee7dfbafc9b6c907af74f7174aa171f4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095702"
---
# <a name="idebugcomplussymbolprovidergetnamefromtoken"></a>IDebugComPlusSymbolProvider::GetNameFromToken
傳回指定之標記的中繼資料物件所關聯的名稱。

## <a name="syntax"></a>語法

```cpp
HRESULT GetNameFromToken (
    IUnknown* pMetadataImport,
    DWORD     dwToken,
    BSTR*     pbstrName
);
```

```csharp
int GetNameFromToken (
    object     pMetadataImport,
    uint       dwToken,
    out string pbstrName
);
```

## <a name="parameters"></a>參數
`pMetadataImport`\
在包含中繼資料資訊的物件。

`dwToken`\
在要命名的權杖。

`pbstrName`\
擴展對應至權杖的名稱。

## <a name="return-value"></a>傳回值
如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="example"></a>範例
下列範例示範如何針對公開 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)介面的 **CDebugSymbolProvider** 物件，執行這個方法。

```cpp
HRESULT CDebugSymbolProvider::GetNameFromToken(
    IUnknown* pMetadataImport,
    DWORD dwToken,
    BSTR* pbstrName
)
{
    HRESULT hr = S_OK;
    CComPtr<IMetaDataImport> pMetaData;

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidInterfacePtr(pMetadataImport, IUnknown));

    METHOD_ENTRY(CDebugSymbolProvider::GetNameFromToken);

    IfFalseGo( pMetadataImport && pbstrName, E_INVALIDARG );

    *pbstrName = NULL;
    IfFailGo( pMetadataImport->QueryInterface( IID_IMetaDataImport,
              (void**) &pMetaData ) );

    switch ( TypeFromToken(dwToken) )
    {
        case mdtModule:
            IfFailGo( GetModuleName( pMetaData, dwToken, pbstrName) );
            break;

        case mdtTypeDef:
            IfFailGo( GetTypeName( pMetaData, dwToken, pbstrName) );
            break;

        case mdtFieldDef:
            IfFailGo( GetFieldName( pMetaData, dwToken, pbstrName) );
            break;

        case mdtMethodDef:
            IfFailGo( GetMethodName( pMetaData, dwToken, pbstrName) );
            break;

        case mdtEvent:
            IfFailGo( GetEventName( pMetaData, dwToken, pbstrName) );
            break;

        case mdtProperty:
            IfFailGo( GetPropertyName( pMetaData, dwToken, pbstrName) );
            break;

        case mdtAssembly:
            IfFailGo( GetAssemblyName( pMetaData, dwToken, pbstrName) );
            break;

        default:
            ASSERT(!"Unsupported token passed to GetNameFromToken");
            hr = E_FAIL;
            break;
    }

Error:

    METHOD_EXIT(CDebugSymbolProvider::GetNameFromToken, hr);
    return hr;
}
```

## <a name="see-also"></a>另請參閱
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
