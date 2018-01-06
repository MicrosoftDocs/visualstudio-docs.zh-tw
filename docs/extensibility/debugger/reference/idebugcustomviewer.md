---
title: "IDebugCustomViewer |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomViewer
helpviewer_keywords: IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9bbe546ffb3c6e61b251e8afbfc7fa9018ffa1b0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
此介面可讓運算式評估工具 (EE) 屬性的值是必要的格式顯示。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugCustomViewer : IUknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 EE 實作這個介面可自訂的格式顯示屬性的值。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 COM 的呼叫`CoCreateInstance`函式具現化這個介面。 `CLSID`傳遞至`CoCreateInstance`取自登錄。 呼叫[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)取得登錄中的位置。 詳細資料，以及您在此範例，請參閱 < 備註 >。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|未指定任何是為了顯示指定的值。|  
  
## <a name="remarks"></a>備註  
 無法顯示屬性的值，以正常方式時，會使用這個介面 — 例如，與資料表或另一種複雜的屬性類型。 自訂檢視器，為表示`IDebugCustomViewer`介面、 不同類型視覺化檢視，這是外部程式，可顯示不論 EE 特定類型的資料。 EE 實作該 EE 特有的自訂檢視器。 使用者選取哪種類型的視覺化檢視，可使用，它的類型視覺化檢視或自訂檢視器。 請參閱[Visualizing 和檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)如需這個程序的詳細資訊。  
  
 自訂檢視器註冊 EE 方式相同，因此，您需要語言 GUID 和零售商 GUID。 確切的度量 （或） 登錄項目名稱只有知道 EE。 此標準會傳入[DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)結構，也就由呼叫[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)。 在標準中所儲存的值是`CLSID`傳遞至 COM 的`CoCreateInstance`函式 （請參閱範例）。  
  
 [SDK 進行偵錯的協助程式](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)函式， `SetEEMetric`，可以用來註冊自訂檢視器。 請參閱 「 運算式評估工具"登錄的`Debugging SDK Helpers`自訂檢視器的特定登錄機碼的需要。 請注意，自訂檢視器必須只有一個公制 （這由 EE 實作者所定義），而運算式評估工具需要使用數個預先定義的度量。  
  
 一般來說，自訂檢視器會提供唯讀資料的檢視，因為[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)介面提供給[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)沒有方法變更為字串，除了屬性的值。 為了支援變更任意資料區塊，EE 實作自訂介面實作在相同物件上`IDebugProperty3`介面。 這個自訂的介面會提供變更的任意資料區塊時所需的方法。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>範例  
 這個範例示範如何從屬性取得的第一個自訂檢視器，如果該屬性有任何自訂檢視器。  
  
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
  
## <a name="see-also"></a>請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [SDK 進行偵錯的協助程式](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)