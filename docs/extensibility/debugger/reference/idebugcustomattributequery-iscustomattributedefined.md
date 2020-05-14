---
title: IDebug自定義屬性查詢::已定義自定義屬性 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCustomAttributeQuery::IsCustomAttributeDefined
- IsCustomAttributeDefined
ms.assetid: c7425db6-4347-4f69-8f88-337ddaa34fa6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3b0be4f8afdfe5320bdf871586f8c0e8f648ae84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732626"
---
# <a name="idebugcustomattributequeryiscustomattributedefined"></a>IDebugCustomAttributeQuery::IsCustomAttributeDefined
確定是否定義了指定的自定義屬性。

## <a name="syntax"></a>語法

```cpp
HRESULT IsCustomAttributeDefined(
    LPCOLESTR pszCustomAttributeName
);
```

```csharp
int IsCustomAttributeDefined(
    string pszCustomAttributeName
);
```

## <a name="parameters"></a>參數
`pszCustomAttributeName`\
[在]自定義屬性的名稱。

## <a name="return-value"></a>傳回值
如果定義了自訂屬性,則傳`S_OK`回 。否則,傳`S_FALSE`回 。

## <a name="example"></a>範例
下面的範例展示如何為公開[IDebugCustom屬性查詢](../../../extensibility/debugger/reference/idebugcustomattributequery.md)介面的**CDebugClassFieldSymbol**物件實現此方法。

```cpp
HRESULT CDebugClassFieldSymbol::IsCustomAttributeDefined(
    LPCOLESTR pszCustomAttribute
)
{
    HRESULT hr = S_FALSE;
    CComPtr<IMetaDataImport> pMetadata;
    mdToken token = mdTokenNil;
    CComPtr<IDebugField> pField;
    CComPtr<IDebugCustomAttributeQuery> pCA;

    ASSERT(IsValidWideStringPtr(pszCustomAttribute));

    METHOD_ENTRY( CDebugClassFieldSymbol::IsCustomAttributeDefined );

    IfFalseGo( pszCustomAttribute, E_INVALIDARG );

    IfFailGo( m_spSH->GetMetadata( m_spAddress->GetModule(), &pMetadata ) );

    IfFailGo( CDebugCustomAttribute::GetTokenFromAddress( m_spAddress, &token) );
    IfFailGo( pMetadata->GetCustomAttributeByName( token,
              pszCustomAttribute,
              NULL,
              NULL ) );
Error:

    METHOD_EXIT( CDebugClassFieldSymbol::IsCustomAttributeDefined, hr );

    if (hr != S_OK)
    {
        hr = S_FALSE;
    }

    return hr;
}
```

## <a name="see-also"></a>另請參閱
- [IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)
