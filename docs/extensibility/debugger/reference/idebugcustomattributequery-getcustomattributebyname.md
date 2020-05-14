---
title: IDebug自定義屬性查詢::按名稱獲取自定義屬性 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCustomAttributeQuery::GetCustomAttributeByName
- GetCustomAttributeByName
ms.assetid: 6779727c-d10a-4abe-9acd-d0a1eb0737e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e1c87fd105d2dbdc18bd4689c4680f2825c9e3be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732636"
---
# <a name="idebugcustomattributequerygetcustomattributebyname"></a>IDebugCustomAttributeQuery::GetCustomAttributeByName
檢索給定其名稱的自定義屬性。

## <a name="syntax"></a>語法

```cpp
HRESULT GetCustomAttributeByName(
    LPCOLESTR pszCustomAttributeName,
    BYTE*     ppBlob,
    DWORD*    pdwLen
);
```

```csharp
int GetCustomAttributeByName(
    string    pszCustomAttributeName,
    ref int[] ppBlob,
    out uint  pdwLen
);
```

## <a name="parameters"></a>參數
`pszCustomAttributeName`\
[在]自定義屬性的名稱。

`ppBlob`\
[in,出]包含自定義屬性數據的位元組。

`pdwLen`\
[出]`ppBlob`參數的長度(以位元組為單位)。

## <a name="return-value"></a>傳回值
如果成功，則傳回 `S_OK`。 如果自訂屬性不存在,請傳`S_FALSE`回 。 否則會傳回錯誤碼。

## <a name="example"></a>範例
下面的範例展示如何為公開[IDebugCustom屬性查詢](../../../extensibility/debugger/reference/idebugcustomattributequery.md)介面的**CDebugClassFieldSymbol**物件實現此方法。

```cpp
HRESULT CDebugClassFieldSymbol::GetCustomAttributeByName(
    LPCOLESTR pszCustomAttributeName,
    BYTE *pBlob,
    DWORD *pdwLen
)
{
    HRESULT hr = S_FALSE;
    CComPtr<IMetaDataImport> pMetadata;
    mdToken token = mdTokenNil;
    CComPtr<IDebugField> pField;
    CComPtr<IDebugCustomAttributeQuery> pCA;

    ASSERT(IsValidWideStringPtr(pszCustomAttributeName));
    ASSERT(IsValidWritePtr(pdwLen, ULONG*));

    METHOD_ENTRY( CDebugClassFieldSymbol::GetCustomAttributeByName );

    IfFalseGo( pszCustomAttributeName && pdwLen, E_INVALIDARG );

    IfFailGo( m_spSH->GetMetadata( m_spAddress->GetModule(), &pMetadata ) );

    IfFailGo( CDebugCustomAttribute::GetTokenFromAddress( m_spAddress, &token) );
    IfFailGo( CDebugCustomAttribute::GetCustomAttributeByName( pMetadata,
              token,
              pszCustomAttributeName,
              pBlob,
              pdwLen ) );
Error:

    METHOD_EXIT( CDebugClassFieldSymbol::GetCustomAttributeByName, hr );
    return hr;
}
```

## <a name="see-also"></a>另請參閱
- [IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)
