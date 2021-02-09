---
title: 編譯單位 |Microsoft Docs
description: 在 Visual Studio debug interface access SDK 中尋找編譯單位符號類型 (SymTagCompiland) 的參考資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- compiland symbol
- compilands, compiland symbol
ms.assetid: c798eb2b-664a-41ec-ae90-5e9d292507ca
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 50000a6cab9981d9450d1aa2b99b86649df04e6f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857414"
---
# <a name="compiland"></a>編譯模組
`SymTagCompiland`連結到 .exe 檔案的每個編譯單位都有一個符號。 編譯單位資訊會在具有標記的符號之間進行分割 `SymTagCompiland` ，您可以在不載入額外的編譯單位符號的情況下抓取符號，也可以使用 `SymTagCompilandDetails` 標記來標記符號，而這可能需要載入其他符號。

## <a name="properties"></a>屬性
 下表顯示對此符號類型有效的屬性。

|屬性|資料類型|描述|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` 如果在編譯時啟用 [編輯後繼續]。|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|.Exe 檔的符號。|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|詞彙父符號的識別碼。|
|[IDiaSymbol::get_libraryName](../../debugger/debug-interface-access/idiasymbol-get-libraryname.md)|`BSTR`|從中載入物件的程式庫或目的檔案名稱。|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|編譯單位之物件檔案的檔案名。|
|[IDiaSymbol::get_sourceFileName](../../debugger/debug-interface-access/idiasymbol-get-sourcefilename.md)|`BSTR`|來源檔案的名稱。|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|傳回 `SymTagCompiland` (其中一個) 的 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md) 值。|

## <a name="see-also"></a>另請參閱
- [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)
- [CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)
- [符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)