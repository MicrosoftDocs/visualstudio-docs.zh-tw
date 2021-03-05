---
description: 抓取一組方法的本機變數版面配置。
title: IDebugComPlusSymbolProvider：： GetLocalVariablelayout |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetLocalVariablelayout
- IDebugComPlusSymbolProvider::GetLocalVariablelayout
ms.assetid: b7328d85-e5e9-4d9f-bcd1-e7711fd33878
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 70b8a8e2e038d8aa60b594b18587c974d863ab89
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167434"
---
# <a name="idebugcomplussymbolprovidergetlocalvariablelayout"></a>IDebugComPlusSymbolProvider::GetLocalVariablelayout
抓取一組方法的本機變數版面配置。

## <a name="syntax"></a>語法

```cpp
HRESULT GetLocalVariablelayout(
    ULONG32   ulAppDomainID,
    GUID      guidModule,
    ULONG32   cMethods,
    _mdToken  rgMethodTokens[],
    IStream** pStreamLayout
);
```

```csharp
int GetLocalVariablelayout(
    uint        ulAppDomainID,
    Guid        guidModule,
    uint        cMethods,
    int[]       rgMethodTokens,
    out IStream pStreamLayout
);
```

## <a name="parameters"></a>參數
`ulAppDomainID`\
在應用程式域的識別碼。

`guidModule`\
在模組的唯一識別碼。

`cMethods`\
在陣列中的方法標記數目 `rgMethodTokens` 。

`rgMethodTokens`\
在方法標記的陣列。

`pStreamLayout`\
擴展包含變數配置的文字資料流程。

## <a name="return-value"></a>傳回值
如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="example"></a>範例
下列範例示範如何針對公開 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)介面的 **CDebugSymbolProvider** 物件，執行這個方法。

```cpp
HRESULT CDebugSymbolProvider::GetLocalVariablelayout(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    ULONG32 cMethods,
    _mdToken rgMethodTokens[],
    IStream** ppStreamLayout)
{
    HRESULT hr = S_OK;

    METHOD_ENTRY(CDebugSymbolProvider::GetLocalVariablelayout);

    CComPtr<ISymUnmanagedReader> symReader;
    IfFailRet(GetSymUnmanagedReader(ulAppDomainID, guidModule, (IUnknown **) &symReader));
    CComPtr<IStream> stream;
    IfFailRet(CreateStreamOnHGlobal(NULL, true, &stream));

    for (ULONG32 iMethod = 0; iMethod < cMethods; iMethod += 1)
    {
        CComPtr<ISymUnmanagedMethod> method;
        IfFailRet(symReader->GetMethod(rgMethodTokens[iMethod], &method));
        CComPtr<ISymUnmanagedScope> rootScope;
        IfFailRet(method->GetRootScope(&rootScope));

        //
        // Add the method's variables to the stream
        //
        IfFailRet(AddScopeToStream(rootScope, 0, stream));

        // do end of method marker
        ULONG32 depth = 0xFFFFFFFF;
        ULONG cb = 0;
        IfFailRet(stream->Write(&depth, sizeof(depth), &cb));
    }

    LARGE_INTEGER pos;
    pos.QuadPart = 0;
    IfFailRet(stream->Seek(pos, STREAM_SEEK_SET, 0));
    *ppStreamLayout = stream.Detach();

    METHOD_EXIT(CDebugSymbolProvider::GetLocalVariablelayout, hr);
    return hr;
}
```

## <a name="see-also"></a>另請參閱
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
