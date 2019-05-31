---
title: IDebugModule3::GetSymbolInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd952242db8b7394fa8915319686ac431b84947d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323942"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
擷取符號，以及每個路徑中搜尋結果中搜尋的路徑的清單。

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
[in]從旗標的組合[SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)列舉型別指定的哪些欄位`pInfo`是要填入。

`pInfo`\
[out]A [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)其成員的指定資訊填入的結構。 如果這會是 null 值，則這個方法會傳回`E_INVALIDARG`。

## <a name="return-value"></a>傳回值
如果方法成功，它會傳回`S_OK`; 否則它會傳回錯誤碼。

> [!NOTE]
> 傳回的字串 (在`MODULE_SYMBOL_SEARCH_INFO`結構) 可能是空的即使`S_OK`會傳回。 在此案例中，是要傳回的任何搜尋資訊。

## <a name="remarks"></a>備註
如果`bstrVerboseSearchInfo`欄位`MODULE_SYMBOL_SEARCH_INFO`結構不是空的則它將包含路徑搜尋和該搜尋結果的清單。 路徑，後面接著省略符號 （"..."），後面接著結果會格式化為清單。 如果有多個路徑的結果組，每一組將分隔"\r\n"（歸位字元-/ 換行） 配對。 模式看起來像這樣：

\<path>...\<result>\r\n\<path>...\<result>\r\n\<path>...\<result>

請注意最後一個項目沒有 \r\n 序列。

## <a name="example"></a>範例
在此範例中，這個方法會傳回具有三個不同的搜尋結果的三個路徑。 每一行都終止歸位字元-/ 換行組。 範例輸出中只會將搜尋結果輸出為單一字串。

> [!NOTE]
> 狀態結果會是 [...] 到該行結尾的正後方的所有項目。

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

**c:\symbols\user32.pdb...找不到的檔案。** 
 **c:\winnt\symbols\user32.pdb...版本不符。** 
 ** \\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb...載入符號。**

## <a name="see-also"></a>另請參閱

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)
- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
