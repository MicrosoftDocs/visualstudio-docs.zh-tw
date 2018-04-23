---
title: IDebugSettingsCallback2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 54724d3e7652df6f7b5b61099136286257fca954
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
啟用偵錯引擎讀取度量設定從遠端。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugSettingsCallback2D : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 這個介面是由偵錯工作階段管理員的事件回呼所實作，且由偵錯引擎。 它也可以使用本機而不是.lib Dbgmetric [d]。  
  
## <a name="methods"></a>方法  
 下表顯示的方法`IDebugSettingsCallback2`。  
  
|方法|描述|  
|------------|-----------------|  
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|列舉可用的運算式評估工具提供的語言和廠商識別碼。|  
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|擷取運算式評估工具本機物件指定度量。|  
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|擷取值，對應至指定的運算式評估工具度量。|  
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|擷取運算式評估工具度量提供檔案的名稱或度量。|  
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|擷取指定之名稱的運算式評估工具度量的唯一識別碼。|  
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|擷取指定之名稱的運算式評估工具公制值字串。|  
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|擷取值，指定其名稱的度量資訊。|  
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|擷取指定之名稱的度量資訊的唯一識別碼。|  
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|擷取指定之名稱的度量值字串。|  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>範例  
 下列範例顯示使用的函式**IDebugSettingsCallback2**物件做為參數。  
  
```cpp  
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