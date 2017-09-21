---
title: "IDebugProgramProvider2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramProvider2"
helpviewer_keywords: 
  - "IDebugProgramProvider2 介面"
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugProgramProvider2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

已註冊的介面可讓工作階段偵錯管理員 」 \(SDM\) 取得的是 「 發行 」 透過程式的相關資訊[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)介面。  
  
## 語法  
  
```  
IDebugProgramProvider2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 會實作這個介面來提供偵錯的程式的相關資訊。  此介面係使用公制登錄 DE 部分中`metricProgramProvider`中所述， [SDK 協助程式進行偵錯](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)。  
  
## 呼叫者的備忘稿  
 呼叫 COM 的`CoCreateInstance`函式與`CLSID`取自登錄的程式提供者。  請參閱範例。  
  
## 方法 Vtable 順序  
  
|方法|描述|  
|--------|--------|  
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|取得有關程式執行，篩選過的各種方式的資訊。|  
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|取得程式\] 節點中，指定一個特定的處理序 id。|  
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|建立用來監看特定類型的處理程序相關聯的提供者事件回呼。|  
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|建立所需的 DE 任何語言特定資源的地區設定。|  
  
## 備註  
 一般情況下，處理程序會使用這個介面，以找出有關該程序中執行的程式。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 範例  
  
```cpp#  
IDebugProgramProvider2 *GetProgramProvider(GUID *pDebugEngineGuid)  
{  
    // This is typically defined globally.  For this example, it is  
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
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [SDK 協助程式進行偵錯](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)