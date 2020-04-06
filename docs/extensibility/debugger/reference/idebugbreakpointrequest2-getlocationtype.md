---
title: IDebug 突破點請求2::獲取位置類型 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2::GetLocationType
helpviewer_keywords:
- IDebugBreakpointRequest2::GetLocationType
ms.assetid: b6d14c59-d3aa-48ff-8278-f6b5bba9c2f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 06bb64190d6821b05ebd638c753bd2b6d3decf71
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734989"
---
# <a name="idebugbreakpointrequest2getlocationtype"></a>IDebugBreakpointRequest2::GetLocationType
獲取此斷點請求的斷點位置類型。

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
[出]從描述此斷點請求位置[的BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md)枚舉中返回值。

## <a name="return-value"></a>傳回值
如果成功,返回`S_OK`;否則,返回錯誤代碼。 如果`E_FAIL`關聯的`bpLocation`[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)結構中的欄位無效,則返回。

## <a name="example"></a>範例
下面的範例展示如何為公開`CDebugBreakpointRequest`[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)介面的簡單物件實現此方法。

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
