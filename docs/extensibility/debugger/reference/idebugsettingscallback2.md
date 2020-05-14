---
title: IDebugSettings 回撥2 |微軟文件
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719934"
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
使調試引擎能夠遠程讀取指標設置。

## <a name="syntax"></a>語法

```
IDebugSettingsCallback2D : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
此介面由會話調試管理器的事件回調實現,並由調試引擎使用。 它也可以在本地使用,而不是Dbgmetric_d_lib。

## <a name="methods"></a>方法
下表顯示的方法`IDebugSettingsCallback2`。

|方法|描述|
|------------|-----------------|
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|枚舉給定語言和供應商識別符的可用運算式賦值器。|
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|檢索給定指標的表達式賦值器本地物件。|
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|檢索對應於表達式賦值器的指定指標的值。|
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|檢索給定名稱或指標的運算式賦值器指標檔。|
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|檢索給定名稱的運算器指標的唯一標識碼。|
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|檢索給定其名稱的運算式賦值器指標的值字串。|
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|檢索給定指標名稱的指標的值。|
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|檢索指標的唯一標識符(給定其名稱)。|
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|檢索給定指標名稱的指標的值字串。|

## <a name="requirements"></a>需求
標題: Msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="example"></a>範例
下面的示例顯示了一個函數,該函數將**IDebugSettingsCallback2**物件作為參數。

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
