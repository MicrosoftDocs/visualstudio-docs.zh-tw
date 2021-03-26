---
description: 這個註冊的介面可讓會話 debug manager (SDM) 取得透過 IDebugProgramPublisher2 介面發行之程式的相關資訊。
title: IDebugProgramProvider2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5bead60e23c708d8a23fcd382b4db0f3f9f7e4c1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065238"
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
這個註冊的介面可讓會話 debug manager (SDM) 取得已透過 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md) 介面「發佈」之程式的相關資訊。

## <a name="syntax"></a>Syntax

```
IDebugProgramProvider2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
Debug engine (DE) 會執行這個介面，以提供所要偵錯工具的相關資訊。 此介面會使用計量在登錄的 DE 區段中進行註冊 `metricProgramProvider` ，如 [用於偵錯工具的 SDK](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)helper 中所述。

## <a name="notes-for-callers"></a>呼叫者注意事項
`CoCreateInstance`使用 `CLSID` 從登錄取得之程式提供者的來呼叫 COM 的函式。 請參閱範例。

## <a name="methods-in-vtable-order"></a>採用 Vtable 順序的方法

|方法|描述|
|------------|-----------------|
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|取得執行之程式的相關資訊，以各種方式進行篩選。|
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|取得特定處理序識別碼的程式節點。|
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|建立回呼，以監看與特定類型進程相關聯的提供者事件。|
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|建立 DE 所需之任何語言特定資源的地區設定。|

## <a name="remarks"></a>備註
一般情況下，程式會使用此介面來找出在該進程中執行的程式。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

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
