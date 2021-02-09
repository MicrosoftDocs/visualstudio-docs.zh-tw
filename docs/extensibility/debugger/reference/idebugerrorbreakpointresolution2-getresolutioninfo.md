---
title: IDebugErrorBreakpointResolution2：： GetResolutionInfo |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpointResolution2::GetResolutionInfo
helpviewer_keywords:
- IDebugErrorBreakpointResolution2::GetResolutionInfo
ms.assetid: d94c4f60-8796-4848-86ee-186bbaa613f5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e43488966017150e5d7e03d7616185e0b619eb4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927024"
---
# <a name="idebugerrorbreakpointresolution2getresolutioninfo"></a>IDebugErrorBreakpointResolution2::GetResolutionInfo
取得中斷點錯誤解析資訊。

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
在 [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) 列舉中的旗標組合，可決定 `pErrorResolutionInfo` 要填寫哪些欄位。

`pErrorResolutionInfo`\
[in，out]以中斷點解析的描述填入的 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) 結構。

## <a name="return-value"></a>傳回值
如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="example"></a>範例
下列範例 `CDebugErrorBreakpointResolution` 會針對公開 [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) 介面的簡單物件，執行這個方法。

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
