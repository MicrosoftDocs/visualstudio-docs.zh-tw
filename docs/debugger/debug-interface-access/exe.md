---
title: Exe | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .dll files
- Exe symbol
- .exe files
- executable files, Exe symbol
ms.assetid: a781d2cf-55fe-4373-9cf1-b732864244e0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 85dc30078565f73d4d2f6cab19c57afade6d8e41
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857269"
---
# <a name="exe"></a>Exe
Exe 是唯一沒有詞法或類別父系的符號，因為它代表 .exe 或 .dll 檔案的全域範圍。 每個檔案只有一個符號具有 `SymTagExe` 標記。 [IDiaSession：： get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)方法會傳回符號。

## <a name="properties"></a>屬性
 下表顯示對此符號類型有效的屬性。

|屬性|資料類型|描述|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|`DWORD`|這個可執行檔的存留期。|
|[IDiaSymbol::get_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|`GUID`|`GUID` 的這個可執行檔。|
|[IDiaSymbol::get_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|`BOOL`|`TRUE` 如果與此可執行檔相關聯的符號檔包含 C 類型 (只有 DIA SDK 8.0 或更新版本) 。|
|[IDiaSymbol::get_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|`BOOL`|`TRUE` 如果已從與這個可執行檔相關聯的符號檔中移除私用符號 (只有 DIA SDK 8.0 或更新版本) 。|
|[IDiaSymbol::get_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|`DWORD`|指出目標 CPU () 的其中一個 [CV_CPU_TYPE_e 列舉](../../debugger/debug-interface-access/cv-cpu-type-e.md) 值的值。|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|.Exe 檔案的名稱。|
|[IDiaSymbol::get_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|`DWORD`|可執行檔的簽章。|
|[IDiaSymbol::get_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|`BSTR`|.Exe 檔 .pdb 或 dbg 檔案的完整路徑。|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|傳回 `SymTagExe` (其中一個) 的 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md) 值。|

## <a name="see-also"></a>另請參閱
- [IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)
- [符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)