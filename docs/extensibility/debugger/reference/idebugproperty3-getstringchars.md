---
description: 抓取與這個屬性相關聯的字串，並將它儲存在使用者提供的緩衝區中。
title: IDebugProperty3：： GetStringChars |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 21baaa5e5eb7446636fcbab9038db87444d50017
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083930"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
抓取與這個屬性相關聯的字串，並將它儲存在使用者提供的緩衝區中。

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
在使用者提供的緩衝區可以容納的最大字元數。

`rgString`\
擴展傳回字串。

 [僅限 c + +] `rgString` 是接收字串 Unicode 字元之緩衝區的指標。 此緩衝區必須至少為 `buflen` 字元) 大小 (不是位元組。

`pceltFetched`\
擴展其中會傳回實際儲存在緩衝區中的字元數。  (可以是 `NULL` c + +。 ) 

## <a name="return-value"></a>傳回值
如果成功，則傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="remarks"></a>備註
在 c + + 中，必須小心確保緩衝區的長度至少為 `buflen` Unicode 字元。 請注意，Unicode 字元的長度為2個位元組。

> [!NOTE]
> 在 c + + 中，傳回的字串不包含終止的 null 字元。 如果有指定， `pceltFetched` 將會指定字串中的字元數。

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
