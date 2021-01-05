---
title: " (Debug 介面存取 SDK) 的常數 |Microsoft Docs"
description: 查看字串常數的清單，這些字串常數可用來透過 (DIA) SDK 的 debug 介面存取，來識別程式偵測資料庫的各種區段 (PDB) 檔。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 806eb9207fa60b7147d1e0d7df75871b23f8850d
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728751"
---
# <a name="constants-debug-interface-access-sdk"></a>常數 (偵錯介面存取 SDK)
這些字串常數可以用來識別程式的各個區段， (PDB 透過 DIA SDK) 檔。

## <a name="constants"></a>常數
下列宣告為 C/c + + 宏。

|巨集|值|
|-----------|-----------|
|`DiaTable_Symbols`|L "符號"|
|`DiaTable_Sections`|L "章節"|
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

## <a name="requirements"></a>規格需求
標頭： dia2。h

## <a name="see-also"></a>請參閱
- [參考](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
