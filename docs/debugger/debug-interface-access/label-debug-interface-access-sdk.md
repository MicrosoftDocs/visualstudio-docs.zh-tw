---
title: 標籤（Debug Interface Access SDK） |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- locations, in program code
- Label symbol
ms.assetid: 8cef7620-5bc8-4500-8bd0-e9e638bccb24
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de9f99f26de3bbd075c00af33b844ed65f4154ce
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461242"
---
# <a name="label-debug-interface-access-sdk"></a>標籤 (偵錯介面存取 SDK)
程式碼中的位置是以符號來識別 `SymTagLabel` 。

## <a name="properties"></a>屬性
 下表顯示對此符號類型有效的屬性。

|屬性|資料類型|描述|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Location 的 Offset 部分;如需詳細資訊，請參閱[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Location 的區段部分;如需詳細資訊，請參閱[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE`如果標籤使用自訂呼叫慣例，則為。|
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE`if 標籤會執行最大的傳回。|
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE`如果標籤包含來自中斷的傳回，則為。|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|封閉式編譯模組、block 或 function 的符號。|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|詞彙父符號的識別碼。|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|標籤具有靜態位置;如需詳細資訊，請參閱[符號位置](../../debugger/debug-interface-access/symbol-locations.md)列舉。|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|標籤的名稱。|
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE`如果標籤是使用[noinline](/cpp/cpp/noinline)屬性指定的，則為。|
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE`如果標籤是使用[noreturn](/cpp/cpp/noreturn)屬性指定的，則為。|
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE`如果永遠不會呼叫標籤。|
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|符號在記憶體中的位移;如需詳細資訊，請參閱[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md) `LocIsRegRel` 。|
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE`如果程式碼具有優化程式碼的 debug 資訊，則為。|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|此標籤在其模組中的相對位置。|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|傳回 `SymTagFuncDebugLabel` （其中一個[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)值）。|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|此標籤在可執行映射中的位置。|

## <a name="see-also"></a>另請參閱
- [符號類型的語彙階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)
- [符號位置](../../debugger/debug-interface-access/symbol-locations.md)