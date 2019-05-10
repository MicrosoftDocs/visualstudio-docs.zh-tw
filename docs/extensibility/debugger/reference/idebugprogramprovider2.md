---
title: IDebugProgramProvider2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2789601c6fd3c10fe1fa11609eaadb7febbd26c1
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457765"
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
這個已註冊的介面可讓偵錯工作階段管理員 (SDM) 取得的是 「 發行 」 透過程式的相關資訊[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)介面。

## <a name="syntax"></a>語法

```
IDebugProgramProvider2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
偵錯引擎 (DE) 會實作這個介面來提供偵錯的程式的相關資訊。 在 [DE] 區段的使用計量的登錄中註冊這個介面`metricProgramProvider`所述，在[偵錯的 SDK 協助程式](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)。

## <a name="notes-for-callers"></a>呼叫端資訊
呼叫 COM 的`CoCreateInstance`函式搭配`CLSID`從登錄取得的程式提供者。 請參閱範例。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法

|方法|描述|
|------------|-----------------|
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|取得程式執行時，在各種不同的方式篩選相關資訊。|
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|取得程式 節點中，指定特定的處理序識別碼。|
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|建立監看的特定類型的處理程序與相關聯的提供者事件的回呼。|
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|建立地區設定以 DE 所需的任何語言特定資源。|

## <a name="remarks"></a>備註
一般而言，處理程序會使用此介面，若要了解該處理序中執行的程式。

## <a name="requirements"></a>需求
標頭： msdbg.h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

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
