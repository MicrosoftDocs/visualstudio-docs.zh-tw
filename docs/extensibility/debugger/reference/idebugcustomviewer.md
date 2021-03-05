---
description: 此介面可讓運算式評估工具 (EE) ，以任何需要的格式來顯示內容的值。
title: IDebugCustomViewer |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8d262869d24c50c543159952506a40be753b4be4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150688"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
此介面可讓運算式評估工具 (EE) ，以任何需要的格式來顯示內容的值。

## <a name="syntax"></a>Syntax

```
IDebugCustomViewer : IUknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
EE 會以自訂格式來執行此介面，以顯示內容的值。

## <a name="notes-for-callers"></a>呼叫者注意事項
呼叫 COM 的函式會將 `CoCreateInstance` 此介面具現化。 `CLSID`傳遞至的 `CoCreateInstance` 會從登錄中取得。 對 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 的呼叫會取得登錄中的位置。 如需詳細資訊和範例，請參閱備註。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
此介面會執行下列方法：

|方法|描述|
|------------|-----------------|
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|執行任何動作，以顯示指定的值。|

## <a name="remarks"></a>備註
當屬性的值無法以一般方式（例如，使用資料表或另一個複雜屬性型別）來顯示時，就會使用這個介面。 自訂檢視器（由介面表示）與 `IDebugCustomViewer` 型別視覺化程式不同，它是一種顯示特定類型資料的外部程式，無論 EE 為何。 EE 會執行該 EE 特定的自訂檢視器。 使用者選取要使用的視覺化類型類型，即為型別視覺化或自訂檢視器。 如需此流程的詳細資料，請參閱 [視覺化和查看資料](../../../extensibility/debugger/visualizing-and-viewing-data.md) 。

自訂檢視器的註冊方式與 EE 相同，因此需要語言 GUID 和廠商 GUID。 確切的度量 (或登錄專案名稱) 只有 EE 才知道。 此計量會在 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) 結構中傳回，而這會由呼叫 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)傳回。 度量中儲存的值是 `CLSID` 傳遞至 COM 函式 `CoCreateInstance` (查看範例) 。

您可以使用 [適用于偵錯工具的 SDK 協助程式](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetEEMetric` 來註冊自訂檢視器。 `Debugging SDK Helpers`如需自訂檢視器所需的特定登錄機碼，請參閱的「運算式評估工具」登錄區段。 請注意，自訂檢視器只需要一個度量 (由 EE 的實作者所定義) 而運算式評估工具則需要數個預先定義的計量。

一般而言，自訂檢視器會提供資料的唯讀視圖，因為提供給[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)的[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)介面沒有任何方法可變更屬性的值，但字串除外。 為了支援變更任意的資料區塊，EE 會在執行介面的相同物件上實作為自訂介面 `IDebugProperty3` 。 然後，這個自訂介面會提供變更任意資料區塊所需的方法。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>範例
這個範例會示範如何從屬性取得第一個自訂檢視器（如果該屬性具有任何自訂檢視器）。

```cpp
IDebugCustomViewer *GetFirstCustomViewer(IDebugProperty2 *pProperty)
{
    // This string is typically defined globally.  For this example, it
    // is defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugCustomViewer *pViewer = NULL;
    if (pProperty != NULL) {
        CComQIPtr<IDebugProperty3> pProperty3(pProperty);
        if (pProperty3 != NULL) {
            HRESULT hr;
            ULONG viewerCount = 0;
            hr = pProperty3->GetCustomViewerCount(&viewerCount);
            if (viewerCount > 0) {
                ULONG viewersFetched = 0;
                DEBUG_CUSTOM_VIEWER viewerInfo = { 0 };
                hr = pProperty3->GetCustomViewerList(0,
                                                     1,
                                                     &viewerInfo,
                                                     &viewersFetched);
                if (viewersFetched == 1) {
                    CLSID clsidViewer = { 0 };
                    CComPtr<IDebugCustomViewer> spCustomViewer;
                    // Get the viewer's CLSID from the registry.
                    ::GetEEMetric(viewerInfo.guidLang,
                                  viewerInfo.guidVendor,
                                  viewerInfo.bstrMetric,
                                  &clsidViewer,
                                  strRegistrationRoot);
                    if (!IsEqualGUID(clsidViewer,GUID_NULL)) {
                        // Instantiate the custom viewer.
                        spCustomViewer.CoCreateInstance(clsidViewer);
                        if (spCustomViewer != NULL) {
                            pViewer = spCustomViewer.Detach();
                        }
                    }
                }
            }
        }
    }
    return(pViewer);
}
```

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [適用於偵錯的 SDK 協助程式](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
