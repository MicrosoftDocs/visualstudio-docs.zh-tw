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
ms.openlocfilehash: 5d2281a82926dabfde88b8d4bb9096f0e9624211
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738524"
---
# <a name="symbols-and-symbol-tags"></a>符號和符號標記
有關已編譯器的 Debug 資訊會儲存在程式資料庫（.pdb）檔案中，做為可使用 Debug Interface Access （DIA） SDK Api 存取的符號。 所有符號都有[IDiaSymbol：： get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)和[IDiaSymbol：： get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)屬性。 @No__t_0 屬性會指出[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)列舉所定義的符號類型。 @No__t_0 屬性是 `DWORD` 值，其中包含符號之每個實例的唯一識別碼。

 符號也具有屬性，可指定符號的其他相關資訊，以及其他符號的參考，最常是[IDiaSymbol：： get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)或[IDiaSymbol：： get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)。 當您查詢包含參考的屬性時，會以[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件的形式傳回參考。 這類屬性一律會與另一個具有相同名稱的屬性搭配使用，但尾碼為 "Id"，例如[IDiaSymbol：： get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)和[IDiaSymbol：： get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)。 符號[位置](../../debugger/debug-interface-access/symbol-locations.md)中的資料表、[符號類型的詞法](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)階層，以及[符號類型的類別](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)階層，會針對每個不同種類的符號列出其屬性。 這些屬性可能有其他符號的相關資訊或參考。 因為 `*Id` 屬性只是其相關屬性的數值序數識別碼，所以會從進一步的討論中省略。 它們只會參考參數澄清所需的位置。

 嘗試存取屬性時，如果沒有發生錯誤，而且已將值指派給 symbol 屬性，則屬性的 "get" 方法會傳回 `S_OK`。 @No__t_0 的傳回值表示屬性對目前的符號無效。

## <a name="in-this-section"></a>本章節內容

[符號位置](../../debugger/debug-interface-access/symbol-locations.md)

描述項號可以擁有的不同位置類型。

[符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)

描述形成詞彙階層的符號類型，例如檔案、模組和函式。

[符號類型的類別階層架構](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)

描述對應至不同語言元素的符號類型，例如類別、陣列和函式傳回類型。

## <a name="see-also"></a>請參閱

- [偵錯介面存取 SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)