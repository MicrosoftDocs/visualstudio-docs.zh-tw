---
title: "IDebugSettingsCallback2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSettingsCallback2 介面"
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSettingsCallback2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

啟用偵錯引擎讀取公制設定遠端。  
  
## 語法  
  
```  
IDebugSettingsCallback2D : IUnknown  
```  
  
## 實作器注意事項  
 這個介面是由事件的回呼工作階段的偵錯管理員實作，由偵錯引擎。  它也可在本機代替 Dbgmetric \[d\].lib。  
  
## 方法  
 下表顯示的方法`IDebugSettingsCallback2`。  
  
|方法|描述|  
|--------|--------|  
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|列舉給定語言和廠商的識別項使用的運算式評估工具。|  
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|擷取運算式評估工具本機物件提供的公制。|  
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|擷取值，對應到指定的度量資訊的運算式評估工具。|  
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|擷取運算式評估工具公制檔案指定名稱\] 或 \[公制。|  
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|擷取運算式評估工具的度量單位，指定其名稱的唯一識別項。|  
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|擷取值的字串指定其名稱的運算式評估工具公制。|  
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|擷取指定其名稱的一個公制值。|  
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|擷取度量單位，指定其名稱的唯一識別的項。|  
|[GetMetricString](../Topic/IDebugSettingsCallback2::GetMetricString.md)|擷取值的字串指定其名稱的公制。|  
  
## 需求  
 標頭: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 範例  
 下列範例會示範的函式 **IDebugSettingsCallback2** 做為參數的物件。  
  
```cpp#  
HRESULT GetDebugSettingsCallback (IDebugSettingsCallback2 **ppCallback)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( ppCallback )  
   {  
        if ( EVAL(m_pdec) )  
            hRes = m_pdec->QueryInterface(IID_IDebugSettingsCallback2, (void **)ppCallback);  
        else  
            hRes = E_FAIL;  
    }  
    else  
        hRes = E_INVALIDARG;  
  
    return ( hRes );  
}  
```