---
title: 函式 （偵錯介面存取 SDK） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Function symbol
ms.assetid: 458dc91c-b78b-4427-84f4-615d89e26760
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5989a2c03c5a6e3f829c0183c797204e3311f5d2
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="function-debug-interface-access-sdk"></a>函式 (偵錯介面存取 SDK)
每個函式由`SymTagFunction`符號。  
  
## <a name="properties"></a>屬性  
 下表顯示適用於此符號類型的屬性。  
  
|屬性|`Data type`|描述|  
|--------------|-----------------|-----------------|  
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|其中一個值的[CV_access_e 列舉](../../debugger/debug-interface-access/cv-access-e.md)，如果函式成員函式。|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|時差部分的位置。如需詳細資訊，請參閱[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|區段組件的位置。如需詳細資訊，請參閱[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|類別，如果函式成員函式的符號。|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|此類別父符號的識別碼。|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE`如果函式會標記為常數。|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE`如果此函數會使用自訂的呼叫慣例 （僅在 DIA SDK V8.0 或更新版本）。|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE`如果函式會執行目前傳回 （只在 DIA SDK V8.0 或更新版本）。|  
|[IDiaSymbol::get_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|`BOOL`|`TRUE`如果此函數會使用配置的記憶體函式 (uinnder DIA SDK V8.0 或更新版本)。|  
|[IDiaSymbol::get_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|`BOOL`|`TRUE`如果函式包含 c + +-樣式例外狀況處理 （只在 DIA SDK V8.0 或更新版本）。|  
|[IDiaSymbol::get_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|`BOOL`|`TRUE`如果函式包含非同步例外狀況處理 （只在 DIA SDK V8.0 或更新版本）。|  
|[IDiaSymbol::get_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|`BOOL`|`TRUE`如果函式包含內嵌組譯碼 （僅在 DIA SDK V8.0 或更新版本）。|  
|[IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|`BOOL`|`TRUE`如果函式包含[longjmp](/cpp/c-runtime-library/reference/longjmp)呼叫 （只在 DIA SDK V8.0 或更新版本）。|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE`如果函式包含 （只在 DIA SDK V8.0 或更新版本） 的安全性檢查。|  
|[IDiaSymbol::get_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|`BOOL`|`TRUE`如果函式包含 Win32 樣式結構化例外狀況處理 （只在 DIA SDK V8.0 或更新版本）。|  
|[IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|`BOOL`|`TRUE`如果函式包含[setjmp](/cpp/c-runtime-library/reference/setjmp)呼叫 （只在 DIA SDK V8.0 或更新版本）。|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE`如果函式傳回插斷 （只在 DIA SDK V8.0 或更新版本）。|  
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|`TRUE`如果函式都是虛擬的簡介。|  
|[IDiaSymbol::get_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|`BOOL`|`TRUE`如果函式已標示為使用其中一個[inline、 __inline、 \__forceinline](/cpp/cpp/inline-functions-cpp)屬性。|  
|[IDiaSymbol::get_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|`BOOL`|`TRUE`如果函式標示為[naked](/cpp/cpp/naked-cpp)屬性 （只在 DIA SDK V8.0 或更新版本）。|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE`如果函式是靜態的 （只在 DIA SDK V8.0 或更新版本）。|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|函式程式碼，從位置開始的位元組數目。|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|封入編譯模組的符號。|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|語彙父符號的識別碼。|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|函式可以具有靜態或中繼資料的位置。如需詳細資訊，請參閱[符號位置](../../debugger/debug-interface-access/symbol-locations.md)。|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|函式的名稱。|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE`如果函式不是內嵌函式 (僅 n DIA SDK V8.0 或更新版本)。|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE`如果函式不可以連線 （只在 DIA SDK V8.0 或更新版本）。|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE`如果函式不會傳回值 （只在 DIA SDK V8.0 或更新版本）。|  
|[IDiaSymbol::get_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|`BOOL`|`TRUE`如果函式編譯緩衝區安全性檢查，但無法完成沒有堆疊順序。|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE`如果您的程式碼偵錯最佳化程式碼 （僅在 DIA SDK V8.0 或更新版本） 的資訊。|  
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|`TRUE`如果函式是純虛擬。|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|此函式的模組中的相對位置。|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|傳回`SymTagFunction`(其中[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)值)。|  
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|函式的中繼資料語彙基元。|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|函式簽章的符號。|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|類型符號的識別碼。|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE`如果函式未對齊。|  
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|`BSTR`|未裝飾的形式的函式名稱 （只能在 DIA SDK v8.0 或更新版本）|  
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|`BSTR`|部分或全部的函式名稱 （只能在 DIA SDK v8.0 或更新版本） 的未裝飾形式。|  
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE`如果虛擬函式。|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|此函式的可執行檔映像的位置。|  
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|如果虛擬函式，然後虛擬函式表中的位移。|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE`如果函式標示為 volatile。|  
  
## <a name="see-also"></a>請參閱  
 [CV_access_e 列舉](../../debugger/debug-interface-access/cv-access-e.md)   
 [符號類型的語彙階層架構](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)   
 [符號位置](../../debugger/debug-interface-access/symbol-locations.md)