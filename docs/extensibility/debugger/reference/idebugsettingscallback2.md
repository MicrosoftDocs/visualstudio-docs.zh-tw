---
title: IDebugSettingsCallback2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c85b54f92970dca5d712b827019300f850b03cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719934"
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
啟用調試引擎以從遠端讀取計量設定。

## <a name="syntax"></a>語法

```
IDebugSettingsCallback2D : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
這個介面是由會話 debug manager 的事件回呼所執行，而且是由偵錯工具引擎使用。 它也可以在本機使用，而不是 Dbgmetric [d] .lib。

## <a name="methods"></a>方法
下表顯示的方法 `IDebugSettingsCallback2` 。

|方法|描述|
|------------|-----------------|
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|使用指定的語言和廠商識別碼，列舉可用的運算式評估工具。|
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|取得給定度量的運算式評估工具區域物件。|
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|抓取對應至運算式評估工具之指定度量的值。|
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|取得指定名稱或計量的運算式評估工具度量檔案。|
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|根據給定的名稱，抓取運算式評估工具度量的唯一識別碼。|
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|抓取運算式評估工具度量的值字串（指定其名稱）。|
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|取得度量的值（指定其名稱）。|
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|使用指定的名稱來抓取度量的唯一識別碼。|
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|取得度量的值字串，並指定其名稱。|

## <a name="requirements"></a>需求
標頭： Msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>範例
下列範例顯示接受 **IDebugSettingsCallback2** 物件做為參數的函式。

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
