---
title: 區塊 | Microsoft Docs
description: 尋找區塊符號類型 (SymTagBlock) 的相關資訊，這會在 Visual Studio debug interface access SDK 的函式中識別嵌套的範圍。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- SymTagBlock symbol
- nested scopes
- Block symbol
ms.assetid: 95b7b0c1-ecc9-405f-8456-5f9cfb866498
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 441f147720a7d9a08422d1633e924d511799393f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857454"
---
# <a name="block"></a>封鎖
每個程式碼區塊都會以 `SymTagBlock` 符號識別。 區塊符號用來識別函式內的嵌套範圍。

## <a name="properties"></a>屬性
 下表顯示對此符號類型有效的屬性。

|屬性|資料類型|描述|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Location 的位移部分;如需詳細資訊，請參閱 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Location 的部分;如需詳細資訊，請參閱 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|區塊中程式碼的位元組數目。|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|封閉區塊或函數的符號。|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|傳回詞彙父符號的識別碼。|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|區塊具有靜態位置;如需詳細資訊，請參閱 [符號位置](../../debugger/debug-interface-access/symbol-locations.md)。|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|傳回區塊 (的名稱，這通常是) 的空字串。|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|傳回這個區塊相對於其詞法父系的虛擬位址。|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|傳回 `SymTagBlock` (其中一個) 的 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md) 值。|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|傳回此區塊在可執行檔中的虛擬位址。|

## <a name="see-also"></a>另請參閱
- [符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)
- [符號位置](../../debugger/debug-interface-access/symbol-locations.md)