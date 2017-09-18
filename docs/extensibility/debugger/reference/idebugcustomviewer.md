---
title: "IDebugCustomViewer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomViewer"
helpviewer_keywords: 
  - "IDebugCustomViewer 介面"
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugCustomViewer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面可讓您的運算式評估工具 \(EE\)，以顯示屬性的值是必要的格式。  
  
## 語法  
  
```  
IDebugCustomViewer : IUknown  
```  
  
## 實作器注意事項  
 EE 會實作這個介面來顯示屬性的值，以自訂的格式。  
  
## 呼叫者的備忘稿  
 COM 的呼叫`CoCreateInstance`函式會具現化這個介面。  `CLSID`傳遞至`CoCreateInstance`取自登錄。  呼叫[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)會取得在登錄中的位置。  如需詳細資訊，以及範例，請參閱 「 備註 」。  
  
## 方法 Vtable 順序  
 這個介面會實作下列方法：  
  
|方法|描述|  
|--------|--------|  
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|沒有項目，即顯示指定的值所需。|  
  
## 備註  
 當慣用的方式將無法顯示屬性的值，這個介面用 — 比方說，與資料表格或其他複雜屬性型別。  自訂的檢視器\]，以表示藉由`IDebugCustomViewer`介面，不同於型別視覺化檢視，也就是外部的程式，以顯示特定的型別，不論得知 ee 給予的資料。  得知 ee 給予實作自訂的檢視器專屬於該 EE。  使用者選取哪一種視覺化檢視來使用，它的型別視覺化檢視或自訂的檢視器。  請參閱[視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)如需這個處理序的詳細資訊。  
  
 自訂的檢視器已登錄為 EE 相同的方式，並且因此，需要一種語言的 GUID 及供應商的 GUID。  只為 EE 已知精確的度量資訊 \(或登錄項目名稱\)。  這個度量資訊會在傳回[DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)結構，依序呼叫會傳回[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)。  計量所儲存的值是`CLSID` ，會傳遞至 COM 的`CoCreateInstance`函式 \(請參閱範例\)。  
  
 [SDK 協助程式進行偵錯](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)函式， `SetEEMetric`，可以用來註冊自訂的檢視器。  請參見"運算式評估工具 」 登錄`Debugging SDK Helpers`自訂的檢視器進行特定的登錄機碼的需要。  請注意，自訂的檢視器必須只有一個計量 \(這就是 EE 實作者所定義\)，而運算式評估工具需要數個預先定義的度量資訊。  
  
 一般情況下，自訂的檢視器提供唯讀檢視的資料，因為[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)介面提供給[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)沒有方法變更為字串的屬性的值除外。  為了支援變更任意的資料區塊，得知 ee 給予會實作自訂的介面，相同的物件實作`IDebugProperty3`介面。  這個自訂介面提供變更任意資料區塊的所需的方法。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 範例  
 這個範例會示範如何從屬性取得第一個自訂的檢視器，如果該屬性有任何自訂的檢視器。  
  
```cpp#  
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
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [SDK 協助程式進行偵錯](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)