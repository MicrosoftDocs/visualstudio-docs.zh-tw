---
title: CompilandDetails |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 34349bf096d8bb98ae4b3de7c7a922b8d28bc4f8
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703005"
---
# <a name="compilanddetails"></a>CompilandDetails
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

編譯模組的資訊分割成具有符號`SymTagCompiland`標記 （低詳細資料） 和`SymTagCompilandDetails`標記 （高詳細資料）。 `SymTagCompilandDetails` 需要載入其他符號。 不過，它提供豐富的資訊不適用於編譯模組`SymTagCompiland`符號。  
  
## <a name="properties"></a>屬性  
 下表顯示適用於此符號類型的屬性。  
  
|屬性|資料類型|描述|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|編譯器後端的組建編號。|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|編譯器後端主要版本號碼。|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|編譯器後端的次要版本號碼。|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|編譯器產生此編譯模組 （只有在 DIA SDK 8.0 版或更新版本） 的名稱。|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` 如果在編譯中已啟用編輯後繼續。|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|編譯器前端的組建編號。|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|編譯器前端的主要版本號碼。|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|編譯器前端的次要版本號碼。|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` 如果此編譯模組的偵錯資訊 （僅在 DIA SDK 8.0 版或更新版本）。|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` 如果此編譯模組中包含 managed 程式碼 （只在 DIA SDK 8.0 版或更新版本）。|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` 如果將編譯模組用來編譯[/GS （緩衝區安全性檢查）](https://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e)編譯器參數 （只在 DIA SDK 8.0 版或更新版本）。|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` 如果編譯模組已從通用中間語言 (CIL) 的程式碼轉換成機器碼。|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` 如果使用者定義型別 (UDT) 具有已對齊記憶體界限 （只在 DIA SDK 8.0 版或更新版本） 指定某些。|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` 如果編譯模組用來編譯[/hotpatch （建立可線上修補的影像）](https://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798)編譯器參數 （只在 DIA SDK 8.0 版或更新版本）。|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` 如果編譯模組用來編譯[/LTCG （連結時間程式碼產生）](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2)編譯器參數 （只在 DIA SDK 8.0 版或更新版本）。|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|如果編譯為 Microsoft Intermediate Language (MSIL) 模組 （只有在 DIA SDK 8.0 版或更新版本），則為 TRUE。|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|原始程式碼語言。|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|編譯模組的符號。|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|語彙父符號的識別碼。|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|編譯模組編譯所在的平台 (其中[CV_CPU_TYPE_e 列舉](../../debugger/debug-interface-access/cv-cpu-type-e.md)值)。|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|傳回`SymTagCompilandDetails`(其中[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)值)。|  
  
## <a name="remarks"></a>備註  
 編譯器通常會在表單，稱為兩階段編譯器;在某些編譯器版本中，每個階段會處理個別的程式。 這些稱為前端和後端編譯器，分別，因此後端與前端的版本號碼的符號屬性。  
  
## <a name="see-also"></a>另請參閱  
 [編譯模組](../../debugger/debug-interface-access/compiland.md)   
 [符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
