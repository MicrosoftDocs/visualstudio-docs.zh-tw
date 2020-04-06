---
title: IDebugErrorBreakpoint決議2::獲取解析度資訊 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpointResolution2::GetResolutionInfo
helpviewer_keywords:
- IDebugErrorBreakpointResolution2::GetResolutionInfo
ms.assetid: d94c4f60-8796-4848-86ee-186bbaa613f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d242dcfac7a9c846793a8dcc9cd6684923192a80
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730031"
---
# <a name="idebugerrorbreakpointresolution2getresolutioninfo"></a>IDebugErrorBreakpointResolution2::GetResolutionInfo
獲取斷點錯誤解決資訊。

## <a name="syntax"></a>語法

```cpp
HRESULT GetResolutionInfo( 
    BPERESI_FIELDS            dwFields,
    BP_ERROR_RESOLUTION_INFO* pErrorResolutionInfo
);
```

```csharp
int GetResolutionInfo( 
    enum_BPERESI_FIELDS        dwFields,
    BP_ERROR_RESOLUTION_INFO[] pErrorResolutionInfo
);
```

## <a name="parameters"></a>參數
`dwFields`\
[在][BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md)枚舉中的標誌的組合,用於確定要填寫`pErrorResolutionInfo`的 欄位。

`pErrorResolutionInfo`\
[進出]用斷點解析度說明填充[BP_ERROR_RESOLUTION_INFO結構。](../../../extensibility/debugger/reference/bp-error-resolution-info.md)

## <a name="return-value"></a>傳回值
如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="example"></a>範例
以下示例為公開`CDebugErrorBreakpointResolution`[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)介面的簡單對象實現此方法。

```cpp
HRESULT CDebugErrorBreakpointResolution::GetResolutionInfo(
    BPERESI_FIELDS dwFields,
    BP_ERROR_RESOLUTION_INFO* pBPErrorResolutionInfo)
{
    HRESULT hr;

    if (pBPErrorResolutionInfo)
    {
        // Copy the specified fields of the request information from the class member
        // variable to the local BP_ERROR_RESOLUTION_INFO variable.
        hr = CopyBP_ERROR_RESOLUTION_INFO(m_bpErrorResolutionInfo,
                                          *pBPErrorResolutionInfo,
                                          dwFields);
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}

HRESULT CDebugErrorBreakpointResolution::CopyBP_ERROR_RESOLUTION_INFO(
    BP_ERROR_RESOLUTION_INFO& bpResSrc,
    BP_ERROR_RESOLUTION_INFO& bpResDest,
    DWORD dwFields)
{
    HRESULT hr = S_OK;

    // Start with a raw copy.
    memcpy(&bpResDest, &bpResSrc, sizeof(BP_ERROR_RESOLUTION_INFO));

    // The fields in the destination is the result of the AND of bpInfoSrc.dwFields
    // and dwFields.
    bpResDest.dwFields = dwFields & bpResSrc.dwFields;

    // Fill in the bp location information if the BPERESI_BPRESLOCATION flag
    // is set in BPERESI_FIELDS.
    if (IsFlagSet(bpResDest.dwFields, BPERESI_BPRESLOCATION))
    {
        // Switch on the BP_TYPE.
        switch (bpResSrc.bpResLocation.bpType)
        {
            case BPT_CODE:
            {
                // AddRef the IDebugCodeContext2 of the BP_RESOLUTION_CODE structure.
                bpResDest.bpResLocation.bpResLocation.bpresCode.pCodeContext->AddRef();
                break;
            }
            case BPT_DATA:
            {
                // Copy the bstrDataExpr, bstrFunc, and bstrImage of the
                // BP_RESOLUTION_DATA structure.
                bpResDest.bpResLocation.bpResLocation.bpresData.bstrDataExpr =
                SysAllocString(bpResSrc.bpResLocation.bpResLocation.bpresData.bstrDataExpr);
                bpResDest.bpResLocation.bpResLocation.bpresData.bstrFunc =
                SysAllocString(bpResSrc.bpResLocation.bpResLocation.bpresData.bstrFunc);
                bpResSrc.bpResLocation.bpResLocation.bpresData.bstrImage =
                SysAllocString(bpResSrc.bpResLocation.bpResLocation.bpresData.bstrImage);
                break;
            }
            default:
            {
                assert(FALSE);
                // Clear the BPERESI_BPRESLOCATION flag of the BPERESI_FIELDS
                // in the destination BP_ERROR_RESOLUTION_INFO.
                ClearFlag(bpResDest.dwFields, BPERESI_BPRESLOCATION);
                break;
            }
        }
    }
    // AddRef the IDebugProgram2 if the BPRESI_PROGRAM flag is set in the BPRESI_FIELDS.
    if (IsFlagSet(bpResDest.dwFields, BPERESI_PROGRAM))
    {
        bpResDest.pProgram->AddRef();
    }
    // AddRef the IDebuThread2 if the BPRESI_THREAD flag is set in the BPRESI_FIELDS.
    if (IsFlagSet(bpResDest.dwFields, BPERESI_THREAD))
    {
        bpResDest.pThread->AddRef();
    }
    // Check if the BPERESI_MESSAGE flag is set in the BPRESI_FIELDS.
    if (IsFlagSet(bpResDest.dwFields, BPERESI_MESSAGE))
    {
        // Copy the source bstrMessage into the destination bstrMessage.
        bpResDest.bstrMessage = SysAllocString(bpResSrc.bstrMessage);
        // Clear the destination flag if there is no message.
        if (!bpResDest.bstrMessage)
        {
            ClearFlag(bpResDest.dwFields, BPERESI_MESSAGE);
        }
    }

    return hr;
}
```

## <a name="see-also"></a>另請參閱

- [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)
- [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
