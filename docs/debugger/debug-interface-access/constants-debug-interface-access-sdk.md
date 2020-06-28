---
title: 常數（Debug Interface Access SDK） |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- constants, DIA SDK
- DIA SDK, constants
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3fa6037253141df1111ef3bc57fac9c718d826dc
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85462236"
---
# <a name="constants-debug-interface-access-sdk"></a>常數 (偵錯介面存取 SDK)
這些字串常數可以透過 DIA SDK，用來識別程式 debug 資料庫（PDB）檔案的各種區段。

## <a name="constants"></a>常數
下列宣告為 C/c + + 宏。

|巨集|值|
|-----------|-----------|
|`DiaTable_Symbols`|L 「符號」|
|`DiaTable_Sections`|L "Sections"|
|`DiaTable_SrcFiles`|L "SourceFiles"|
|`DiaTable_LineNums`|L"LineNumbers"|
|`DiaTable_SegMap`|L"SegmentMap"|
|`DiaTable_Dbg`|L"Dbg"|
|`DiaTable_InjSrc`|L "InjectedSource"|
|`DiaTable_FrameData`|L"FrameData"|

## <a name="example"></a>範例
以下是使用其中一個符號的範例：

```C++
HRESULT GetSymbolTable(IDiaEnumTables *pEnumTables, IDiaTable **pTable)
{
    HRESULT hr;
    VARIANT var;
    var.vt      = VT_BSTR;
    var.bstrVal = SysAllocString( DiaTable_Symbols );
    hr = pEnumTables->Item( var, pTable );
    return(hr);
}
```

## <a name="requirements"></a>需求
標頭： dia2。h

## <a name="see-also"></a>另請參閱
- [參考](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
