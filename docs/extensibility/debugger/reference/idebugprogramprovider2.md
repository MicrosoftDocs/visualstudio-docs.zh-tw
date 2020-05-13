---
title: IDebug程式提供程式2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 43557e5d81e5140967a1189e57a350595d0f7220
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721701"
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
此已註冊的介面允許工作階段調試管理員 (SDM) 獲取有關透過[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)介面"發佈"的程式的資訊。

## <a name="syntax"></a>語法

```
IDebugProgramProvider2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
除錯引擎 (DE) 實現此介面,以提供有關正在除錯的程式的資訊。 此介面使用指標`metricProgramProvider`在註冊表的 DE 部分註冊,如[用於調試的 SDK 幫助器](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)中所述。

## <a name="notes-for-callers"></a>通話備註
使用`CLSID`從註冊表獲取`CoCreateInstance`的程式提供程式呼叫 COM 的功能。 請參閱示例。

## <a name="methods-in-vtable-order"></a>依 Vtable 順序排列的方法

|方法|描述|
|------------|-----------------|
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|獲取有關以各種方式運行、篩選的程式的資訊。|
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|獲取程式節點,給定特定的進程 ID。|
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|建立回調以監視與特定類型的進程關聯的提供程式事件。|
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|為 DE 所需的任何特定於語言的資源建立區域設置。|

## <a name="remarks"></a>備註
通常,程式使用此介面來瞭解該進程中運行的程式。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="example"></a>範例

```cpp
IDebugProgramProvider2 *GetProgramProvider(GUID *pDebugEngineGuid)
{
    // This is typically defined globally. For this example, it is
    // defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugProgramProvider2 *pProvider = NULL;
    if (pDebugEngineGuid != NULL) {
        CLSID clsidProvider = { 0 };
        ::GetMetric(NULL,
                    metrictypeEngine,
                    *pDebugEngineGuid,
                    metricProgramProvider,
                    &clsidProvider,
                    strRegistrationRoot);
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {
            CComPtr<IDebugProgramProvider2> spProgramProvider;
            spProgramProvider.CoCreateInstance(clsidProvider);
            if (spProgramProvider != NULL) {
                pProvider = spProgramProvider.Detach();
            }
        }
    }
    return(pProvider);
}
```

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [適用於偵錯的 SDK 協助程式](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
