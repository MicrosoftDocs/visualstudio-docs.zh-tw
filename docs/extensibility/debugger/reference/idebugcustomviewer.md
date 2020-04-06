---
title: IDebug自定義檢視器 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c44d2289180ece35725b9258e9d20abeb3a4cac3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732426"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
此介面使運算式賦值器 (EE) 能夠以任何必要的格式顯示屬性的值。

## <a name="syntax"></a>語法

```
IDebugCustomViewer : IUknown
```

## <a name="notes-for-implementers"></a>實施者說明
EE 實現此介面以自訂格式顯示屬性的值。

## <a name="notes-for-callers"></a>通話備註
對 COM 函`CoCreateInstance`數的調用會實例化此介面。 傳遞給`CLSID``CoCreateInstance`的是從註冊表獲取的。 對[GetCustomViewerList 的](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)調用獲取註冊表中的位置。 有關詳細資訊,請參閱備註以及示例。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
此介面實現以下方法:

|方法|描述|
|------------|-----------------|
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|執行顯示給定值所需的一切。|

## <a name="remarks"></a>備註
當屬性的值不能通過正常方式(例如,使用數據表或其他複雜屬性類型)顯示時,使用此介面。 自定義查看器(由`IDebugCustomViewer`介面表示)與類型可視化器不同,後者是顯示特定類型數據的外部程式,而不考慮 EE。 EE 實現特定於該 EE 的自訂檢視器。 用戶選擇要使用的可視化工具類型,無論是類型可視化工具還是自定義查看器。 有關此過程的詳細資訊[,請參閱可視化和查看資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)。

自訂檢視器的註冊方式與 EE 相同,因此需要語言 GUID 和供應商 GUID。 只有 EE 知道確切的指標(或註冊表條目名稱)。 此指標在[DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)結構中返回,而該結構又通過調用[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)返回。 指標中儲存的值是`CLSID`傳遞給 COM 函`CoCreateInstance`數的值 (請參閱範例)。

[用於調試](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)`SetEEMetric`功能的 SDK 幫助器 可用於註冊自訂檢視器。 有關自定義查看器所需的特定註冊表項,請參閱`Debugging SDK Helpers`的「表達式評估器」註冊表部分。 請注意,自定義查看器只需要一個指標(由 EE 的實現者定義),而表達式賦值器需要多個預定義的指標。

通常,自定義查看器提供數據的唯讀檢視,因為提供給[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)的[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)介面除了作為字串外,沒有任何方法來更改屬性的值。 為了支援更改任意資料塊,EE 在`IDebugProperty3`實現 介面的同一對象上實現了自定義介面。 然後,此自定義介面將提供更改任意數據塊所需的方法。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="example"></a>範例
此示例演示如何從屬性獲取第一個自定義查看器(如果該屬性具有任何自定義查看器)。

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
