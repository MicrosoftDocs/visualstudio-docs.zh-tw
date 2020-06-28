---
title: 符號類型的詞法階層 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b003fcbd1b38eb5dc919b7f4f361e0b56b585f08
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461221"
---
# <a name="lexical-hierarchy-of-symbol-types"></a>符號類型的語彙階層架構
下表顯示 [詞彙] 階層中的符號類型。

## <a name="symbol-types"></a>符號類型

|符號類型|描述|
|-----------------|-----------------|
|[批註](../../debugger/debug-interface-access/annotation.md)|指定程式碼中的標注位置。|
|[封鎖](../../debugger/debug-interface-access/block.md)|指定函數中的嵌套範圍。|
|`Compiland`|指定 `compiland` 連結到 .exe 檔案的。|
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|指定可能需要載入其他編譯模組詳細資料，因而產生要取得之執行時間額外負荷的編譯模組資料。|
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|指定編譯模組編譯所需的任何其他環境變數。|
|[Custom (偵錯介面存取 SDK)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|指定使用者定義的符號。|
|[資料 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|將這類變數指定為參數、本機變數、全域變數和類別成員。|
|[Convert.exe](../../debugger/debug-interface-access/exe.md)|指定資料的全域範圍;對應至整個 .exe 或 .dll 檔案。|
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|指定一個函式，該函式具有要結束偵錯工具的已定義點。|
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|指定一個函式，該函式具有要開始偵錯工具的已定義點。|
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