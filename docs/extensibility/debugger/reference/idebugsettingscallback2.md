---
title: IDebugSettingsCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3dea6edb6045e21931651ff5c20a01a5f000ff62
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722677"
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
啟用偵錯引擎讀取計量設定從遠端。

## <a name="syntax"></a>語法

```
IDebugSettingsCallback2D : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
此介面是藉由將工作階段的偵錯管理員事件回呼，並供偵錯引擎。 它也可以使用在本機而不是.lib Dbgmetric [d]。

## <a name="methods"></a>方法
下表顯示的方法`IDebugSettingsCallback2`。

|方法|描述|
|------------|-----------------|
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|列舉可用的運算式評估工具提供的語言和廠商識別碼。|
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|擷取指定度量的運算式的評估工具本機物件。|
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|擷取對應至的運算式評估工具的指定計量的值。|
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|擷取運算式評估工具計量提供檔案名稱或計量。|
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|擷取指定其名稱的運算式評估工具計量的唯一識別碼。|
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|擷取指定其名稱的運算式評估工具度量的值字串。|
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|擷取值，指定其名稱的度量資訊。|
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|擷取指定其名稱的度量的唯一識別碼。|
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|擷取值字串，指定其名稱的度量。|

## <a name="requirements"></a>需求
標頭：Msdbg.h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>範例
下列範例示範使用的函式**IDebugSettingsCallback2**物件做為參數。

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
