---
title: IDebugmodule3::獲取符號資訊 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3aafb28715f58eaba4499b47a2e1dee15b82ed14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726898"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
檢索搜索符號的路徑清單以及搜索每個路徑的結果。

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
[在][SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)枚舉中的標誌的組合,指定要填充`pInfo`哪些 欄位。

`pInfo`\
[出][一個MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)結構,其成員要用指定的資訊填充。 如果這是 null 值,則此方法`E_INVALIDARG`將傳回 。

## <a name="return-value"></a>傳回值
如果方法成功,它將傳`S_OK`回 。否則,它將返回一個錯誤代碼。

> [!NOTE]
> 即使`S_OK`返回,返回的字串`MODULE_SYMBOL_SEARCH_INFO`(在結構中)也可能為空。 在這種情況下,沒有要返回的搜索資訊。

## <a name="remarks"></a>備註
`bstrVerboseSearchInfo`如果`MODULE_SYMBOL_SEARCH_INFO`結構欄位不為空,則它包含搜索的路徑列表和該搜索的結果。 清單的格式採用路徑,後跟省略號 ("..."),後跟結果。 如果有多個路徑結果對,則每對由一對"\r\n"(回車/換行)對分隔。 模式如下所示:

\<路徑>...\<結果>\r\n\<路徑>...\<結果>\r\n\<路徑>...\<結果>

請注意,最後一個條目沒有 \r\n 序列。

## <a name="example"></a>範例
在此示例中,此方法返回三個具有三個不同搜尋結果的路徑。 每行都用回車/換行對終止。 範例輸出將搜尋結果列印為單個字串。

> [!NOTE]
> 狀態結果是"..."到行的末尾。

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

**c:\符號\使用者32.pdb...找不到檔。**
 **c:\winnt\符號\user32.pdb...版本不匹配。**
[符號 **]符號\user32.dll_0a8sd0ad8ad_user32.pdb... \\已載入符號。**

## <a name="see-also"></a>另請參閱

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)
- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
