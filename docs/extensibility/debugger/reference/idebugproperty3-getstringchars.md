---
title: IDebug屬性3::獲取字串字元 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 693a29bc30ef206428713ace36275389de1b7f0a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721090"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
檢索與此屬性關聯的字串,並將其存儲在使用者提供的緩衝區中。

## <a name="syntax"></a>語法

```cpp
HRESULT GetStringChars(
    ULONG  buflen,
    WCHAR* rgString,
    ULONG* pceltFetched
);
```

```csharp
int GetStringChars(
    uint       buflen,
    out string rgString,
    out uint   pceltFetched
);
```

## <a name="parameters"></a>參數
`buflen`\
[在]使用者提供的緩衝區可以保留的最大字元數。

`rgString`\
[出]返回字串。

 [C++僅`rgString`],是指向接收字串 Unicode 字元的緩衝區的指標。 此緩衝區的大小必須至少`buflen`為字元(而不是位元組)。

`pceltFetched`\
[出]返回緩衝區中實際存儲的字元數。 (可在`NULL`C++。

## <a name="return-value"></a>傳回值
如果成功,返回`S_OK`;否則返回錯誤代碼。

## <a name="remarks"></a>備註
在C++時,必須注意確保緩衝區至少`buflen`為 Unicode 字元長。 請注意,Unicode 字元長 2 位元組。

> [!NOTE]
> 在C++,返回的字串不包括終止空字元。 如果給定,`pceltFetched`將指定字串中的字元數。

## <a name="example"></a>範例

```cpp
CStringW RetrievePropertyString(IDebugProperty2 *pPropInfo)
{
    CStringW returnString = L"";
    CComQIPtr<IDebugProperty3> pProp3 = pPropInfo->pProperty;
    If (pProp3 != NULL) {
        ULONG dwStrLen = 0;
        HRESULT hr;
        hr = pProp3->GetStringCharLength(&dwStrLen);
        if (SUCCEEDED(hr) && dwStrLen > 0) {
            ULONG dwRead;
            CStrBufW buf(returnString,dwStrLen,CStrBuf::SET_LENGTH);
            hr = pProp3->GetStringChars(dwStrLen,
                                        reinterpret_cast<WCHAR*>(static_cast<CStringW::PXSTR>(buf)),
                                        &dwRead);
        }
    }
    return(returnString);
}
```

## <a name="see-also"></a>另請參閱
- [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
