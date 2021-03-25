---
description: 取得此中斷點要求的中斷點位置型別。
title: IDebugBreakpointRequest2：： GetLocationType |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2::GetLocationType
helpviewer_keywords:
- IDebugBreakpointRequest2::GetLocationType
ms.assetid: b6d14c59-d3aa-48ff-8278-f6b5bba9c2f3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1bd254d5bfd9126a65ad7364212f628b1b45cb61
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054513"
---
# <a name="idebugbreakpointrequest2getlocationtype"></a>IDebugBreakpointRequest2::GetLocationType
取得此中斷點要求的中斷點位置型別。

## <a name="syntax"></a>語法

```cpp
HRESULT GetLocationType(
    BP_LOCATION_TYPE* pBPLocationType
);
```

```csharp
int GetLocationType(
    out enum_BP_LOCATION_TYPE pBPLocationType
);
```

## <a name="parameters"></a>參數
`pBPLocationType`\
擴展傳回 [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) 列舉中的值，這個值會描述此中斷點要求的位置。

## <a name="return-value"></a>傳回值
如果成功，則傳回， `S_OK` 否則傳回錯誤碼。 `E_FAIL`如果 `bpLocation` 相關聯的[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)結構中的欄位無效，則傳回。

## <a name="example"></a>範例
下列範例顯示如何針對 `CDebugBreakpointRequest` 公開[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) 介面的簡單物件，執行這個方法。

```
HRESULT CDebugBreakpointRequest::GetLocationType(BP_LOCATION_TYPE* pBPLocationType)
{
    HRESULT hr;

    if (pBPLocationType)
    {
        // Set default BP_LOCATION_TYPE.
        *pBPLocationType = BPLT_NONE;

        // Check if the BPREQI_BPLOCATION flag is set in BPREQI_FIELDS.
        if (IsFlagSet(m_bpRequestInfo.dwFields, BPREQI_BPLOCATION))
        {
            // Get the new BP_LOCATION_TYPE.
            *pBPLocationType = m_bpRequestInfo.bpLocation.bpLocationType;
            hr = S_OK;
        }
        else
        {
            hr = E_FAIL;
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>另請參閱
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
