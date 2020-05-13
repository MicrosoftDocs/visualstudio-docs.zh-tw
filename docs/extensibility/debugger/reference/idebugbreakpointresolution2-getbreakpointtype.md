---
title: IDebug 突破點決議2::獲取斷點類型 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointResolution2::GetBreakpointType
helpviewer_keywords:
- IDebugBreakpointResolution2::GetBreakpointType
ms.assetid: 2b707fb9-f703-4c78-91bf-7434f57790a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2949366eeb3e79a732e94a4a8f8e9912048c6452
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734818"
---
# <a name="idebugbreakpointresolution2getbreakpointtype"></a>IDebugBreakpointResolution2::GetBreakpointType
獲取此解析度表示的斷點的類型。

## <a name="syntax"></a>語法

```cpp
HRESULT GetBreakpointType( 
    BP_TYPE* pBPType
);
```

```csharp
int GetBreakpointType( 
    out enum_ BP_TYPE pBPType
);
```

## <a name="parameters"></a>參數
`pBPType`\
[出]從[BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)枚舉中返回指定此斷點類型的值。

## <a name="return-value"></a>傳回值
如果成功,返回`S_OK`;否則返回錯誤代碼。 如果關聯的BP_RESOLUTION_INFO結構`bpResLocation`中的欄位無效[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md), 則傳回E_FAIL。

## <a name="remarks"></a>備註
例如,斷點可以是代碼或數據斷點。

## <a name="example"></a>範例
下面的範例展示如何為公開`CDebugBreakpointResolution`[IDebugBreakpointE2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)介面的簡單物件實現此方法。

```
HRESULT CDebugBreakpointResolution::GetBreakpointType(BP_TYPE* pBPType)
{
    HRESULT hr;

    if (pBPType)
    {
        // Set default BP_TYPE.
        *pBPType = BPT_NONE;

        // Check if the BPRESI_BPRESLOCATION flag is set in BPRESI_FIELDS.
        if (IsFlagSet(m_bpResolutionInfo.dwFields, BPRESI_BPRESLOCATION))
        {
            // Set the new BP_TYPE.
            *pBPType = m_bpResolutionInfo.bpResLocation.bpType;
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
- [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
