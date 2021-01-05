---
title: CompilandDetails |Microsoft Docs
description: 在 Visual Studio debug interface access SDK 中尋找 CompilandDetails 符號類型 (SymTagCompilandDetails) 的參考資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 04687eb58ecee2211f098c0f432afc28e0465305
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728778"
---
# <a name="compilanddetails"></a>CompilandDetails
編譯單位資訊會在具有標記的符號之間分割 `SymTagCompiland` (低詳細資料) 和 `SymTagCompilandDetails` 標記 (高詳細資料) 。 `SymTagCompilandDetails` 提供有關符號無法使用之編譯單位的豐富資訊 `SymTagCompiland` 。

## <a name="properties"></a>屬性
 下表顯示對此符號類型有效的屬性。

|屬性|資料類型|描述|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|編譯器的後端組建編號。|
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|編譯器的後端主要版本號碼。|
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|編譯器的後端次要版本號碼。|
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|產生此編譯單位之編譯器的名稱， (只有 DIA SDK 8.0 或更新版本) 。|
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` 如果在編譯時啟用 [編輯後繼續]。|
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|編譯器的前端組建編號。|
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|編譯器的前端主要版本號碼。|
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|編譯器的前端次要版本號碼。|
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` 如果這個編譯單位只有 DIA SDK 8.0 或更新版本) 中 (的 debug 資訊。|
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` 如果此編譯單位只包含 DIA SDK 8.0 或更新版本) 中的 managed 程式碼 (。|
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` 如果已使用 [/gs (緩衝區安全性檢查 ](/cpp/build/reference/gs-buffer-security-check) 來編譯編譯單位，) 編譯器參數僅 (DIA SDK 8.0 或更新版本) 。|
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` 如果編譯單位是從常見的中繼語言 (CIL) 程式碼轉換成機器碼。|
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` 如果使用者定義型別 (UDT) 已對齊 DIA SDK 8.0 或更新版本) 中的某些特定記憶體界限 (。|
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` 如果編譯單位是使用/hotpatch 編譯的， [ (建立可線上修補映射) ](/cpp/build/reference/hotpatch-create-hotpatchable-image) 編譯器參數只 (DIA SDK 8.0 版或更新版本) 。|
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` 如果編譯單位是以 [/ltcg (連結時產生程式碼，) ](/cpp/build/reference/ltcg-link-time-code-generation) 編譯器參數 (只在 DIA SDK 8.0 或更新版本的) 中。|
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|如果編譯單位是 Microsoft 中繼語言 (MSIL) 模組 (僅限 DIA SDK 8.0 或更新版本的) 。|
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|原始程式碼語言。|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|編譯單位的符號。|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|詞彙父符號的識別碼。|
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|編譯編譯單位的平臺 (其中一個 [CV_CPU_TYPE_e 列舉](../../debugger/debug-interface-access/cv-cpu-type-e.md) 值) 。|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|傳回 `SymTagCompilandDetails` (其中一個) 的 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md) 值。|

## <a name="remarks"></a>備註
 編譯器通常會以兩種形式提供，稱為雙 pass 編譯器;在某些編譯器版本中，每個階段都是由個別的程式來處理。 這些分別稱為前端和後端編譯器，因此是後端和前端版本號碼的符號屬性。

## <a name="see-also"></a>請參閱
- [編譯模組](../../debugger/debug-interface-access/compiland.md)
- [符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)