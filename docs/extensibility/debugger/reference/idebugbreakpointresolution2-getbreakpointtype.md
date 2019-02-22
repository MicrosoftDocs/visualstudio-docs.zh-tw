---
title: IDebugBreakpointResolution2::GetBreakpointType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 91d1321e99705bd4173edacb13c99223c10eb2d1
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "56413510"
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
[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)  
[BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)  
[BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)  
[BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)  
[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
