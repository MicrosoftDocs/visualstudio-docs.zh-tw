---
title: 符號和符號標記 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 72f4cb4b6ed35e880e1cb26980420f4e951ffc16
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471216"
---
# <a name="symbols-and-symbol-tags"></a>符號和符號標記
偵錯資訊編譯的程式儲存在程式資料庫 (.pdb) 檔，做為可使用偵錯介面存取 (DIA) SDK Api 的符號。 所有符號[idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)和[idiasymbol:: Get_symindexid](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)屬性。 `symTag`屬性指示符號的類型所定義的[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)列舉型別。 `symIndexId`屬性是`DWORD`含有符號的每個執行個體的唯一識別碼值。  
  
 符號也有屬性，可以指定其他相關資訊符號，以及其他符號，參考最常[idiasymbol:: Get_lexicalparent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)或[idiasymbol:: Get_classparent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). 當您查詢包含參考的屬性時，做為傳回的參考[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件。 這類屬性會永遠搭配使用另一個屬性名稱相同但後面加上具有 「 識別碼 」，例如[idiasymbol:: Get_lexicalparentid](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)和[idiasymbol:: Get_classparentid](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)。 中的資料表[符號位置](../../debugger/debug-interface-access/symbol-locations.md)，[語彙階層的符號類型](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)，和[類別階層架構的符號類型](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)概述各種不同類型的每個屬性的符號。 這些屬性可能會有相關資訊或其他符號的參考。 因為`*Id`屬性都只是數值的序數識別項，其相關的屬性，它們會省略進一步討論。 它們就是只在所需的參數資訊。  
  
 當嘗試存取屬性，如果沒有發生錯誤，而且已指派的符號屬性的值，屬性的"get"方法會傳回`S_OK`。 傳回值為`S_FALSE`指出屬性不是有效的目前符號。  
  
## <a name="in-this-section"></a>本節內容  
 [符號位置](../../debugger/debug-interface-access/symbol-locations.md)  
 描述不同種類的可以有一個符號的位置。  
  
 [符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 描述表單語彙階層架構，例如檔案、 模組和函式的符號類型。  
  
 [符號類型的類別階層架構](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 描述對應至不同的語言項目，例如類別、 陣列和函式傳回類型的符號類型。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯介面存取 SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)