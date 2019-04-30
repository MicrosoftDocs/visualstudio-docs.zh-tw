---
title: 符號和符號標記 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6affc24a84ef4d008ece5f95e45a11eb70f33b4e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62854705"
---
# <a name="symbols-and-symbol-tags"></a>符號和符號標記
偵錯資訊編譯的程式儲存在程式資料庫 (.pdb) 檔案，做為可使用偵錯介面存取 (DIA) SDK Api 的符號。 所有的符號[idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)並[idiasymbol:: Get_symindexid](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)屬性。 `symTag`所定義的屬性會指出符號種類[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)列舉型別。 `symIndexId`屬性是`DWORD`包含符號的每個執行個體的唯一識別項的值。

 符號也會有屬性可指定的其他資訊的符號，以及參考其他符號，最常[idiasymbol:: Get_lexicalparent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)或[idiasymbol:: Get_classparent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). 當您查詢包含參考的屬性時，做為傳回參考[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件。 這類屬性會一律搭配使用另一個屬性相同的名稱，但後面加上具有 「 識別碼 」，例如[idiasymbol:: Get_lexicalparentid](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)並[idiasymbol:: Get_classparentid](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)。 中的資料表[符號位置](../../debugger/debug-interface-access/symbol-locations.md)，[語彙階層的符號類型](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)，並[類別階層架構的符號類型](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)不同種類的每個說明屬性的符號。 這些屬性可能的相關資訊或其他符號的參考。 因為`*Id`屬性都只是數值的序數識別項，其相關的屬性，它們會省略進一步討論。 其參考只在所需的參數說明。

 若要存取屬性，如果未發生錯誤，而且已指派的符號屬性值時，屬性的"get"方法會傳回`S_OK`。 傳回值為`S_FALSE`指出屬性不是適用於目前的符號。

## <a name="in-this-section"></a>本節內容

[符號位置](../../debugger/debug-interface-access/symbol-locations.md)

說明不同的類型可以有一個符號的位置。

[符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)

描述形成語彙階層架構，例如檔案、 模組和函式的符號類型。

[符號類型的類別階層架構](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)

描述對應至不同的語言項目，例如類別、 陣列和函式傳回類型的符號類型。

## <a name="see-also"></a>另請參閱

- [偵錯介面存取 SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)