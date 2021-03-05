---
description: 所有變數（例如參數、區域變數、全域變數和類別成員）都是透過 SymTagData 符號來識別。
title: Data (Debug Interface Access SDK) |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- global variables [C++], as symbols
- local variables [C++], as symbols
- class members [C++], as symbols
- Data symbol
ms.assetid: 0f17e96a-2e06-42c9-a877-3e5e670ee0ef
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 08354e2f54a8c4d4e96d139470494dcdefe78703
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149288"
---
# <a name="data-debug-interface-access-sdk"></a>資料 (偵錯介面存取 SDK)
所有變數（例如參數、區域變數、全域變數和類別成員）都是以符號來識別 `SymTagData` 。 您 `LocIsConstant` 也可以使用此類型來識別常數值 () 。

## <a name="properties"></a>屬性
 下表顯示對此符號類型有效的屬性。

|屬性|資料類型|描述|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|如果是欄位，則為 [CV_access_e 列舉](../../debugger/debug-interface-access/cv-access-e.md)的其中一個值。|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Location 的位移部分;如需詳細資訊，請參閱 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Location 的部分;如需詳細資訊，請參閱 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|
|[IDiaSymbol::get_addressTaken](../../debugger/debug-interface-access/idiasymbol-get-addresstaken.md)|`BOOL`|`TRUE` 如果另一個符號參考此資料的位址。|
|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)|`DWORD`|Location 的位位置;如需詳細資訊，請參閱 DIA SDK 8.0 版中不支援的 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md) () 。|
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|類別的符號，如果這是結構、等位或類別欄位，則為。|
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|類別父系符號的識別碼。|
|[IDiaSymbol::get_compilerGenerated](../../debugger/debug-interface-access/idiasymbol-get-compilergenerated.md)|`BOOL`|`TRUE` 如果資料是由編譯器所產生。|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` 如果資料標示為常數。|
|[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|`DWORD`|其中一個 [DataKind 的列舉](../../debugger/debug-interface-access/datakind.md) 值。|
|[IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)|`BOOL`|`TRUE` 如果資料是匯總資料類型的一部分 (只有在 DIA SDK 8.0 版和更新版本中) 。|
|[IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)|`BOOL`|`TRUE` 如果資料已分割成多個符號的匯總， (只有 DIA SDK 8.0 和更新版本) 。|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|位位的長度;如需詳細資訊，請參閱 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|封閉編譯單位、function 或 block 的符號。|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|詞彙父符號的識別碼。|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|任何允許的位置類型;如需詳細資訊，請參閱 [符號位置](../../debugger/debug-interface-access/symbol-locations.md)|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|變數的名稱。|
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|自註冊內容的位移;如需詳細資訊，請參閱 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|
|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|`DWORD`|註冊位置的指示項;如需詳細資訊，請參閱 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|資料在其區塊內的相對位置。|
|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|`DWORD`|取得資料的插槽號碼。|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|傳回 `SymTagData` (其中一個) 的 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md) 值。|
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|代表資料的元資料標記。|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|變數類型的符號。|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|變數型別符號的識別碼。|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` 如果資料未對齊。|
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|`VARIANT`|常數資料的值。|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|資料在可執行檔中的位置。|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` 如果資料標示為 volatile。|

## <a name="see-also"></a>另請參閱
- [CV_access_e 列舉](../../debugger/debug-interface-access/cv-access-e.md)
- [DataKind 列舉](../../debugger/debug-interface-access/datakind.md)
- [符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)
- [符號位置](../../debugger/debug-interface-access/symbol-locations.md)
