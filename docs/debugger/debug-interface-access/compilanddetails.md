---
title: CompilandDetails |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b72a5ae53c336877c68cc9b164cf787017dacbe2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745411"
---
# <a name="compilanddetails"></a>CompilandDetails
編譯模組資訊會在具有 `SymTagCompiland` 標記（低詳細資料）和 `SymTagCompilandDetails` 標記（高詳細資料）的符號之間分割。 `SymTagCompilandDetails` 需要載入其他符號。 不過，它提供了 `SymTagCompiland` 符號無法使用之編譯模組的豐富資訊。

## <a name="properties"></a>內容
 下表顯示對此符號類型有效的屬性。

|屬性|資料類型|描述|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|編譯器的後端組建編號。|
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|編譯器的後端主要版本號碼。|
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|編譯器的後端次要版本號碼。|
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|產生此編譯模組的編譯器名稱（僅限 DIA SDK 8.0 或更新版本）。|
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` 是否在編譯時啟用 [編輯後繼續]。|
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|編譯器的前端組建編號。|
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|編譯器的前端主要版本號碼。|
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|編譯器的前端次要版本號碼。|
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` 此編譯模組是否有 debug 資訊（僅適用于 DIA SDK 的8.0 版或更新版本）。|
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` 此編譯模組是否包含 managed 程式碼（僅適用于 DIA SDK 的8.0 版或更新版本）。|
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` 如果編譯模組是以[/gs （緩衝區安全性檢查）](/cpp/build/reference/gs-buffer-security-check)編譯器參數編譯（僅在 DIA SDK 8.0 或更新版本中）。|
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|如果編譯模組是從通用中繼語言（CIL）程式碼轉換為機器碼，則 `TRUE`。|
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` 使用者定義型別（UDT）是否已對齊某個指定的記憶體界限（僅限在 DIA SDK 8.0 版或更新版本中）。|
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` 如果編譯模組是使用[/hotpatch （Create 可線上修補 Image）](/cpp/build/reference/hotpatch-create-hotpatchable-image)編譯器參數（僅在 DIA SDK 8.0 或更新版本中）編譯。|
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|如果編譯模組是使用[/ltcg （連結時間程式碼產生）](/cpp/build/reference/ltcg-link-time-code-generation)編譯器參數（僅在 DIA SDK 8.0 或更新版本中）進行編譯，則為 `TRUE`。|
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|如果編譯模組是 Microsoft 中繼語言（MSIL）模組（僅在 DIA SDK 8.0 或更新版本中），則為 TRUE。|
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|原始程式碼語言。|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|編譯模組的符號。|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|詞彙父符號的識別碼。|
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|編譯編譯模組的平臺（其中一個[CV_CPU_TYPE_e 列舉](../../debugger/debug-interface-access/cv-cpu-type-e.md)值）。|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|傳回 `SymTagCompilandDetails` （其中一個[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)值）。|

## <a name="remarks"></a>備註
 編譯器通常是一種稱為兩階段式編譯器的形式;在某些編譯器版本中，每個階段都是由個別的程式處理。 這些分別稱為前端和後端編譯器，因此是後端和前端版本號碼的符號屬性。

## <a name="see-also"></a>請參閱
- [編譯模組](../../debugger/debug-interface-access/compiland.md)
- [符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)