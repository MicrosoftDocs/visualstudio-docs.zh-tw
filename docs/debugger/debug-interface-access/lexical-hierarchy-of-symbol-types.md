---
description: 下表顯示 [詞彙] 階層中的符號類型。
title: 符號類型的詞法階層 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 605b16d2a53178b52095e9919c10bba53f3f21a1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155387"
---
# <a name="lexical-hierarchy-of-symbol-types"></a>符號類型的語彙階層架構
下表顯示 [詞彙] 階層中的符號類型。

## <a name="symbol-types"></a>符號類型

|符號類型|描述|
|-----------------|-----------------|
|[註釋](../../debugger/debug-interface-access/annotation.md)|在程式碼中指定已標注的位置。|
|[封鎖](../../debugger/debug-interface-access/block.md)|在函數中指定嵌套的範圍。|
|`Compiland`|指定 `compiland` 連結到 .exe 檔案的。|
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|指定可能需要載入額外編譯單位詳細資料的編譯單位資料，因而產生執行時間額外負荷來取得。|
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|指定任何額外的環境變數，對編譯單位的編譯相當重要。|
|[Custom (偵錯介面存取 SDK)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|指定使用者定義的符號。|
|[資料 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|以參數、區域變數、全域變數和類別成員的形式指定這些變數。|
|[Exe](../../debugger/debug-interface-access/exe.md)|指定資料的全域範圍;對應至整個 .exe 或 .dll 檔案。|
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|指定一個函式，此函式具有已定義的結束時間點。|
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|指定一個函式，此函式具有已定義的開始偵錯工具點。|
|[函式 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|指定函數。|
|[標籤 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|指定程式碼中的位置。|
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|指定建立可執行程式時所顯示的外部符號。|
|[Thunk](../../debugger/debug-interface-access/thunk.md)|指定 `thunk` 。|
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|指定 `namespace` 識別碼。|

> [!NOTE]
> 視符號類型而定，可能會有其他符號屬性可用。 這些屬性會列在個別的符號主題中。

## <a name="see-also"></a>另請參閱
- [符號類型的類別階層架構](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
- [符號和符號標記](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)
