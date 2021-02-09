---
title: 函式 () Debug 介面存取 SDK 的功能 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Function symbol
ms.assetid: 458dc91c-b78b-4427-84f4-615d89e26760
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a294444cf03760ef83fb02ae012bcbf609a2982a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857248"
---
# <a name="function-debug-interface-access-sdk"></a>函式 (偵錯介面存取 SDK)
每個函式都是以符號來識別 `SymTagFunction` 。

## <a name="properties"></a>屬性
 下表顯示對此符號類型有效的屬性。

|屬性|資料類型|描述|
|--------------|-----------------|-----------------|
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|如果函數是成員函式，則為 [CV_access_e 列舉](../../debugger/debug-interface-access/cv-access-e.md)的其中一個值。|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Location 的位移部分;如需詳細資訊，請參閱 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Location 的部分;如需詳細資訊，請參閱 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|如果函數是成員函式，則為類別的符號。|
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|類別父系符號的識別碼。|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` 如果函式標示為常數。|
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` 如果函式使用自訂呼叫慣例， (只有 DIA SDK 8.0 或更新版本) 。|
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` 如果函式只會在 DIA SDK 8.0 或更新版本) 中執行 (。|
|[IDiaSymbol::get_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|`BOOL`|`TRUE` 如果函式使用配置的記憶體函數 (只有 uinnder DIA SDK 8.0 或更新版本) 。|
|[IDiaSymbol::get_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|`BOOL`|`TRUE` 如果函式包含 c + + 樣式例外狀況處理 (只有 DIA SDK 8.0 或更新版本) 。|
|[IDiaSymbol::get_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|`BOOL`|`TRUE` 如果函式只包含 DIA SDK 8.0 或更新版本) 中的非同步例外狀況處理 (。|
|[IDiaSymbol::get_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|`BOOL`|`TRUE` 如果函式包含內嵌元件 (DIA SDK 8.0 或更新版本) 。|
|[IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|`BOOL`|`TRUE` 如果函式包含 [longjmp](/cpp/c-runtime-library/reference/longjmp) 呼叫， (只有 DIA SDK 8.0 或更新版本) 。|
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` 如果函式包含安全性檢查， (只有 DIA SDK 8.0 或更新版本) 。|
|[IDiaSymbol::get_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|`BOOL`|`TRUE` 如果函式包含 Win32 樣式的結構化例外狀況處理 (只有 DIA SDK 8.0 或更新版本) 。|
|[IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|`BOOL`|`TRUE` 如果函式包含 [setjmp](/cpp/c-runtime-library/reference/setjmp) 呼叫 (只有 DIA SDK 8.0 或更新版本) 。|
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` 如果函式只有在 DIA SDK 8.0 或更新版本) 中的中斷 (。|
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|`TRUE` 如果函數為簡介虛擬。|
|[IDiaSymbol::get_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|`BOOL`|`TRUE` 如果函式已標記其中一個 [內嵌、__inline \_ _forceinline](/cpp/cpp/inline-functions-cpp) 屬性。|
|[IDiaSymbol::get_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|`BOOL`|`TRUE` 如果函式是以 [naked](/cpp/cpp/naked-cpp) 屬性標示 (只有 DIA SDK 8.0 或更新版本) 。|
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE` 如果函式是靜態 (只有 DIA SDK 8.0 或更新版本) 。|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|函式程式碼的位元組數目，從位置開始算起。|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|封閉編譯單位的符號。|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|詞彙父符號的識別碼。|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|函數可以有靜態或中繼資料位置;如需詳細資訊，請參閱 [符號位置](../../debugger/debug-interface-access/symbol-locations.md)。|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|函數的名稱。|
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` 如果函式不是內嵌函數 (只有 n DIA SDK 8.0 或更新版本) 。|
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` 如果無法觸達函式 (DIA SDK 8.0 或更新版本) 。|
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` 如果函式不會傳回值， (只有 DIA SDK 8.0 或更新版本) 。|
|[IDiaSymbol::get_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|`BOOL`|`TRUE` 如果函式是以緩衝區安全性檢查編譯，但是無法完成堆疊排序。|
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` 如果程式碼只有 DIA SDK 8.0 或更新版本) 中的優化程式碼的 debug 資訊 (。|
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|`TRUE` 如果函式是純虛擬的，則為。|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|此函式在其模組中的相對位置。|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|傳回 `SymTagFunction` (其中一個) 的 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md) 值。|
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|函數的元資料標記。|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|函數簽章的符號。|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|類型符號的識別碼。|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` 如果函式未對齊。|
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|`BSTR`|函式名稱的未裝飾形式只 (DIA SDK 8.0 或更新版本中) |
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|`BSTR`|只有 DIA SDK 8.0 或更新版本) 的部分或所有未修飾形式的函式名稱 (。|
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE` 如果虛擬函式。|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|此函式在可執行映射中的位置。|
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|如果虛擬函數，則為虛擬函式資料表中的位移。|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` 如果函數標示為 volatile。|

## <a name="see-also"></a>另請參閱
- [CV_access_e 列舉](../../debugger/debug-interface-access/cv-access-e.md)
- [符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)
- [符號位置](../../debugger/debug-interface-access/symbol-locations.md)