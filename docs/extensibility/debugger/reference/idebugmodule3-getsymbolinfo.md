---
description: 抓取搜尋符號的路徑清單，以及搜尋每個路徑的結果。
title: IDebugModule3：： GetSymbolInfo |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9cc4c8d7c88e4b973ad7055327da73472a6ed4d2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065524"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
抓取搜尋符號的路徑清單，以及搜尋每個路徑的結果。

## <a name="syntax"></a>語法

```cpp
HRESULT GetSymbolInfo(
    SYMBOL_SEARCH_INFO_FIELDS  dwFields,
    MODULE_SYMBOL_SEARCH_INFO* pInfo
);
```

```csharp
int GetSymbolInfo(
    enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,
    MODULE_SYMBOL_SEARCH_INFO[]    pinfo
);
```

## <a name="parameters"></a>參數
`dwFields`\
在 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) 列舉中的旗標組合，指定 `pInfo` 要填入的欄位。

`pInfo`\
擴展要以指定的資訊填入其成員的 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) 結構。 如果這是 null 值，則這個方法會傳回 `E_INVALIDARG` 。

## <a name="return-value"></a>傳回值
如果方法成功，則會傳回， `S_OK` 否則會傳回錯誤碼。

> [!NOTE]
> 即使傳回，在結構) 中傳回的字串 (`MODULE_SYMBOL_SEARCH_INFO` 也可能是空的 `S_OK` 。 在此情況下，沒有要傳回的搜尋資訊。

## <a name="remarks"></a>備註
如果 `bstrVerboseSearchInfo` 結構的欄位 `MODULE_SYMBOL_SEARCH_INFO` 不是空的，則它會包含搜尋的路徑清單以及該搜尋的結果。 此清單的格式為路徑，後面接著省略號 ( "..." ) ，後面接著結果。 如果有一個以上的路徑結果配對，則每一組都會以 "\r\n" (換行字元) 組分隔。 模式看起來像這樣：

\<path>...\<result>\r\n \<path> \<result> .。。\r\n \<path> .。。\<result>

請注意，最後一個專案沒有 \r\n 順序。

## <a name="example"></a>範例
在此範例中，這個方法會傳回三個不同搜尋結果的路徑。 每一行都會以換行鍵/換行字元組來終止。 範例輸出只會將搜尋結果列印成單一字串。

> [!NOTE]
> 狀態結果是緊接在「...」之後的所有專案最高到行尾。

```cpp
void ShowSymbolSearchResults(IDebugModule3 *pIDebugModule3)
{
    MODULE_SYMBOL_SEARCH_INFO ssi = { 0 };
    HRESULT hr;
    hr = pIDebugModule3->GetSymbolInfo(SSIF_VERBOSE_SEARCH_INFO,&ssi);
    if (SUCCEEDED(hr)) {
        CComBSTR searchInfo = ssi.bstrVerboseSearchInfo;
        if (searchInfo.Length() != 0) {
            std::wcout << (wchar_t *)(BSTR)searchInfo;
            std::wcout << std::endl;
        }
    }
}
```

**c:\symbols\user32.pdb.。。找不到檔案。** 
**c:\winnt\symbols\user32.pdb.。。版本不相符。** 
**\\\symbols\symbols\user32.dll \0a8sd0ad8ad\user32.pdb.。。已載入符號。**

## <a name="see-also"></a>另請參閱

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)
- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
