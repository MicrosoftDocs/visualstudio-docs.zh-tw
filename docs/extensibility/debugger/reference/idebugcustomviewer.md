---
title: IDebugCustomViewer |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46561bbab71b12d924edec96650736c8b1576894
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328023"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
此介面可讓運算式評估工具 (EE) 中是必要的任何格式顯示屬性的值。

## <a name="syntax"></a>語法

```
IDebugCustomViewer : IUknown
```

## <a name="notes-for-implementers"></a>實作者的附註
EE 會實作這個介面可自訂的格式顯示屬性的值。

## <a name="notes-for-callers"></a>呼叫端資訊
COM 的呼叫`CoCreateInstance`函式具現化這個介面。 `CLSID`傳遞至`CoCreateInstance`取自登錄。 呼叫[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)取得登錄中的位置。 如需詳細資訊，以及範例，請參閱 < 備註 >。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
這個介面會實作下列方法：

|方法|描述|
|------------|-----------------|
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|沒有所能顯示指定的值。|

## <a name="remarks"></a>備註
無法顯示屬性的值，以正常方式時，會使用這個介面 — 例如，使用資料表或另一種複雜屬性類型。 自訂檢視器，表示由`IDebugCustomViewer`介面中，不同於類型視覺化檢視，也就是外部程式，可顯示 EE 不論特定類型的資料。 EE 實作該 EE 專屬自訂檢視器。 使用者選取哪種類型的視覺化檢視來使用，類型視覺化檢視或自訂的檢視器。 請參閱[視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)如需此程序的詳細資訊。

自訂檢視器中 EE 的相同方式來註冊，並因此需要語言 GUID 和廠商的 GUID。 確切的計量 （或登錄項目名稱） 只有知道 EE。 此標準會傳入[DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)結構，也就由呼叫[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)。 儲存在計量的值是`CLSID`傳遞至 COM 的`CoCreateInstance`函式 （請參閱範例）。

[SDK 協助程式進行偵錯](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)函式， `SetEEMetric`，可用來註冊自訂的檢視器。 請參閱 「 運算式評估工具 」 登錄的`Debugging SDK Helpers`自訂檢視器所需要的特定登錄機碼。 請注意，自訂檢視器必須只有一個計量 （這由 EE 的實作者所定義），而運算式評估工具需要使用數個預先定義的度量。

一般來說，自訂檢視器提供唯讀資料的檢視，因為[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)介面提供給[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)沒有變更以外的屬性的值，做為字串的方法。 為了支援變更任意資料區塊，EE 會實作自訂介面實作的相同物件上`IDebugProperty3`介面。 這個自訂的介面會接著提供變更的任意資料區塊所需的方法。

## <a name="requirements"></a>需求
標頭： msdbg.h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>範例
此範例示範如何從屬性取得的第一個自訂檢視器，如果該屬性的任何自訂檢視器。

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
