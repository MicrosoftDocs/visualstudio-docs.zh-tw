---
title: FuncDebugStart |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- FuncDebugStart symbol
- debugging [DIA SDK], start point
ms.assetid: 1cbc6ca5-87d0-4c30-a39e-0a9dc62ce1a9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8cdc450c020cd0c8f192becfb861b118422b9ce5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53963977"
---
# <a name="funcdebugstart"></a>FuncDebugStart
如果函式具有定義的時間點，在哪一個偵錯開始時，點由使用的符號就是`SymTagFuncDebugStart`標記。  
  
## <a name="properties"></a>屬性  
 下表顯示適用於此符號類型的屬性。  
  
|屬性|資料類型|說明|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|時差的部分的位置;如需詳細資訊，請參閱 < [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|區段組件的位置;如需詳細資訊，請參閱 < [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` 如果此函數會使用自訂的呼叫慣例 （只在 DIA SDK 8.0 版或更新版本）。|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` 如果函式會傳回目前執行 （只有在 DIA SDK 8.0 版或更新版本）。|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` 如果函式包含傳回插斷 （只在 DIA SDK 8.0 版或更新版本）。|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE` 如果函式標記為 static （只在 DIA SDK 8.0 版或更新版本）。|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|封入函式的符號。|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|語彙父符號的識別碼。|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|起始點具有靜態位置;如需詳細資訊，請參閱 <<c0> [ 符號位置](../../debugger/debug-interface-access/symbol-locations.md)。|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` 如果函式所指定的[noinline](/cpp/cpp/noinline) （只在 DIA SDK 8.0 版或更新版本） 的屬性。|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` 如果函式所指定的[noreturn](/cpp/cpp/noreturn) （只在 DIA SDK 8.0 版或更新版本） 的屬性。|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` 如果 （只在 DIA SDK 8.0 版或更新版本），絕不會呼叫此函式。|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|在記憶體中; 符號的位移如需詳細資訊，請參閱 < [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)， `LocIsRegRel`。|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` 如果程式碼為 （只在 DIA SDK 8.0 版或更新版本） 最佳化的程式碼的偵錯資訊。|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|在其區塊的函式的相對位置。|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|傳回`SymTagFuncDebugStart`(其中[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)值)。|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|可執行檔內的函式的位置。|  
  
## <a name="see-also"></a>請參閱  
 [符號類型的語彙階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)   
 [符號位置](../../debugger/debug-interface-access/symbol-locations.md)