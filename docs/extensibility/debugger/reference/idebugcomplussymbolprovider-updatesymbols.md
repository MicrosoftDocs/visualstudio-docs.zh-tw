---
title: IDebugComPlus符號提供者::更新符號 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- UpdateSymbols
- IDebugComPlusSymbolProvider::UpdateSymbols
ms.assetid: d530f6f1-4af2-454b-bab0-02478a8fe81e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 20a4fa6f6ec52ee556bd62fe303d0e21e4c56d6a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733498"
---
# <a name="idebugcomplussymbolproviderupdatesymbols"></a>IDebugComPlusSymbolProvider::UpdateSymbols
使用指定數據流中的調試符號更新記憶體中的調試符號。

## <a name="syntax"></a>語法

```cpp
HRESULT UpdateSymbols (
    ULONG32  ulAppDomainID,
    GUID     guidModule,
    IStream* pUpdateStream
);
```

```csharp
int UpdateSymbols (
    uint    ulAppDomainID,
    Guid    guidModule,
    IStream pUpdateStream
);
```

## <a name="parameters"></a>參數
`ulAppDomainID`\
[在]應用程式域的標識碼。

`guidModule`\
[在]模組的唯一標識碼。

`pUpdateStream`\
[在]包含更新的調試符號的數據流。

## <a name="example"></a>範例
下面的範例展示如何為公開[IDebugComPlusSymbol提供程式](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)介面的**CDebugSymbol提供程式**物件實現此方法。

```cpp
HRESULT CDebugSymbolProvider::UpdateSymbols(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    IStream* pUpdateStream
)
{
    ASSERT(!"Use UpdateSymbols2 on IDebugENCSymbolProvider2");
    return E_NOTIMPL;
}

HRESULT CDebugSymbolProvider::UpdateSymbols2(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    IStream* pUpdateStream,
    LINEDELTA* pDeltaLines,
    ULONG cDeltaLines
)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pModule;
    Module_ID idModule(ulAppDomainID, guidModule);

    METHOD_ENTRY( CDebugSymbolProvider::UpdateSymbols );

    IfFailGo( GetModule( idModule, &pModule ) );
    IfFailGo( pModule->UpdateSymbols( pUpdateStream, pDeltaLines, cDeltaLines ) );

Error:

    METHOD_EXIT( CDebugSymbolProvider::UpdateSymbols, hr );

    return hr;
}
```

## <a name="return-value"></a>傳回值
如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="see-also"></a>另請參閱
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
