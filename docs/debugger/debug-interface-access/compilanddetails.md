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
ms.openlocfilehash: b0bcedda06119149413895415272c1a18934bce7
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85280825"
---
# <a name="compilanddetails"></a>CompilandDetails
編譯模組資訊會在具有 `SymTagCompiland` 標記（低詳細資料）和 `SymTagCompilandDetails` 標記（高細節）的符號之間分割。 `SymTagCompilandDetails`提供與符號不提供之編譯模組相關的豐富資訊 `SymTagCompiland` 。

## <a name="properties"></a>屬性
 下表顯示對此符號類型有效的屬性。

|屬性|資料類型|描述|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|編譯器的後端組建編號。|
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|編譯器的後端主要版本號碼。|
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|編譯器的後端次要版本號碼。|
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|產生此編譯模組的編譯器名稱（僅限 DIA SDK 8.0 或更新版本）。|
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE`如果已在編譯時啟用 [編輯後繼續]。|
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|編譯器的前端組建編號。|
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|編譯器的前端主要版本號碼。|
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|編譯器的前端次要版本號碼。|
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE`如果此編譯模組具有 debug 資訊（僅在 DIA SDK 8.0 或更新版本中）。|
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE`如果此編譯模組包含 managed 程式碼（僅限 DIA SDK 8.0 或更新版本）。|
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE`如果編譯模組是以[/gs （緩衝區安全性檢查）](/cpp/build/reference/gs-buffer-security-check)編譯器參數編譯（僅在 DIA SDK 8.0 或更新版本中）。|
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE`如果編譯模組是從通用中繼語言（CIL）程式碼轉換為機器碼，則為。|
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE`如果使用者定義型別（UDT）已經對齊某個指定的記憶體界限（僅在 DIA SDK 的8.0 或更新版本中）。|
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE`如果編譯模組是使用[/hotpatch （建立可線上修補映射）](/cpp/build/reference/hotpatch-create-hotpatchable-image)編譯器參數（僅限 DIA SDK 8.0 或更新版本）所編譯。|
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE`如果編譯模組是以[/ltcg （連結時間程式碼產生）](/cpp/build/reference/ltcg-link-time-code-generation)編譯器參數編譯（僅在 DIA SDK 8.0 或更新版本中）。|
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|如果編譯模組是 Microsoft 中繼語言（MSIL）模組（僅在 DIA SDK 8.0 或更新版本中），則為 TRUE。|
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|原始程式碼語言。|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|編譯模組的符號。|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|詞彙父符號的識別碼。|
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|編譯編譯模組的平臺（其中一個[CV_CPU_TYPE_e 列舉](../../debugger/debug-interface-access/cv-cpu-type-e.md)值）。|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|傳回 `SymTagCompilandDetails` （其中一個[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)值）。|

## <a name="remarks"></a>備註
 編譯器通常是一種稱為兩階段式編譯器的形式;在某些編譯器版本中，每個階段都是由個別的程式處理。 這些分別稱為前端和後端編譯器，因此是後端和前端版本號碼的符號屬性。

## <a name="see-also"></a>另請參閱
- [編譯模組](../../debugger/debug-interface-access/compiland.md)
- [符號類型的語彙階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)