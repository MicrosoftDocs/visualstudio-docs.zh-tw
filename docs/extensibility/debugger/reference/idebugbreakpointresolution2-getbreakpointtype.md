---
title: IDebugBreakpointResolution2::GetBreakpointType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointResolution2::GetBreakpointType
helpviewer_keywords:
- IDebugBreakpointResolution2::GetBreakpointType
ms.assetid: 2b707fb9-f703-4c78-91bf-7434f57790a0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ab8bc16da26b1c47ecdda79db361e24b68e2e82
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62876884"
---
# <a name="idebugbreakpointresolution2getbreakpointtype"></a>IDebugBreakpointResolution2::GetBreakpointType
取得由這個解決方案的中斷點類型。

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

#### <a name="parameters"></a>參數
`pBPType`

 [out]傳回值，以從[BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)列舉，指定此中斷點的類型。

## <a name="return-value"></a>傳回值
如果成功，則傳回`S_OK`; 否則會傳回錯誤碼。 傳回 E_FAIL`bpResLocation`欄位相關聯[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)結構無效。

## <a name="remarks"></a>備註
中斷點可能是程式碼或資料中斷點，例如。

## <a name="example"></a>範例
下列範例示範如何實作這個方法來簡單`CDebugBreakpointResolution`公開的物件[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)介面。

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
