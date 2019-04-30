---
title: 編譯模組 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- compiland symbol
- compilands, compiland symbol
ms.assetid: c798eb2b-664a-41ec-ae90-5e9d292507ca
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ecdd4284e4c7c417af6ebd935418d56cf601bb74
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62555257"
---
# <a name="compiland"></a>編譯模組
有一個`SymTagCompiland`符號針對每個編譯模組的已連結至.exe 檔案。 編譯模組的資訊分割成具有符號`SymTagCompiland`標記，可以擷取而不需要載入其他的編譯模組符號和符號與`SymTagCompilandDetails`標記，這可能需要載入其他符號。

## <a name="properties"></a>屬性
 下表顯示適用於此符號類型的屬性。

|屬性|資料類型|描述|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` 如果在編譯時啟用編輯後繼續。|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|.Exe 檔案的符號。|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|語彙父符號的識別碼。|
|[IDiaSymbol::get_libraryName](../../debugger/debug-interface-access/idiasymbol-get-libraryname.md)|`BSTR`|物件已從載入的文件庫或物件檔案名稱。|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|編譯模組的物件檔案的檔案名稱。|
|[IDiaSymbol::get_sourceFileName](../../debugger/debug-interface-access/idiasymbol-get-sourcefilename.md)|`BSTR`|原始程式檔的名稱。|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|傳回`SymTagCompiland`(其中[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)值)。|

## <a name="see-also"></a>另請參閱
- [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)
- [CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)
- [符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)