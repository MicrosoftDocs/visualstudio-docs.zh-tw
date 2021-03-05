---
description: 已編譯器的 Debug 資訊會儲存在程式資料庫 ( .pdb) 檔中，做為可使用 Debug 介面存取 (DIA) SDK Api 存取的符號。
title: 符號和符號標記 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 98631149e5a53c13bfc9b12b0d6de165c345e29a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155282"
---
# <a name="symbols-and-symbol-tags"></a>符號和符號標記
已編譯器的 Debug 資訊會儲存在程式資料庫 ( .pdb) 檔中，做為可使用 Debug 介面存取 (DIA) SDK Api 存取的符號。 所有符號都有 [IDiaSymbol：： get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) 和 [IDiaSymbol：： get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) 屬性。 `symTag`屬性工作表示[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)列舉所定義的符號種類。 `symIndexId`屬性是一個 `DWORD` 值，其中包含每個符號實例的唯一識別碼。

 符號的屬性也可以指定符號的其他相關資訊，以及其他符號的參考，最常是 [IDiaSymbol：： get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) 或 [IDiaSymbol：： get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)。 當您查詢包含參考的屬性時，參考會以 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 物件的形式傳回。 這類屬性一律會與另一個具有相同名稱的屬性配對，但尾碼為 "Id"，例如， [IDiaSymbol：： get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) 和 [IDiaSymbol：： get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)。 符號 [位置](../../debugger/debug-interface-access/symbol-locations.md)中的資料表、 [符號類型的詞法](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)階層，以及 [符號類型的類別](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) 階層，會針對每個不同種類的符號來概述其屬性。 這些屬性可能會有有關或參考其他符號的相關資訊。 因為 `*Id` 屬性只是其相關屬性的數值序數識別碼，所以會從進一步的討論中省略它們。 它們只是參考參數說明所需的位置。

 嘗試存取屬性時，如果沒有發生錯誤，而且已將值指派給 symbol 屬性，則屬性的 "get" 方法會傳回 `S_OK` 。 的傳回值 `S_FALSE` 表示屬性對目前的符號而言是不正確。

## <a name="in-this-section"></a>本節內容

[符號位置](../../debugger/debug-interface-access/symbol-locations.md)

描述項號可以有的不同位置種類。

[符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)

描述形成詞彙階層的符號類型，例如檔案、模組和函式。

[符號類型的類別階層架構](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)

描述對應至不同語言專案（例如類別、陣列和函式傳回類型）的符號類型。

## <a name="see-also"></a>另請參閱

- [偵錯介面存取 SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
