---
title: FuncDebugStart | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- FuncDebugStart symbol
- debugging [DIA SDK], start point
ms.assetid: 1cbc6ca5-87d0-4c30-a39e-0a9dc62ce1a9
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 19c2192df89c532a615a4b5298fbf6e39669c4f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65692294"
---
# <a name="funcdebugstart"></a>FuncDebugStart
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

如果函式已定義開始進行偵錯工具的定義點，則該點會由具有標記的符號來識別 `SymTagFuncDebugStart` 。  
  
## <a name="properties"></a>屬性  
 下表顯示對此符號類型有效的屬性。  
  
|屬性|資料類型|描述|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Location 的位移部分;如需詳細資訊，請參閱 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Location 的部分;如需詳細資訊，請參閱 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` 如果函式使用自訂呼叫慣例， (只有 DIA SDK 8.0 或更新版本) 。|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` 如果函式只會在 DIA SDK 8.0 或更新版本) 中執行 (。|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` 如果函式包含從中斷的傳回 (只有 DIA SDK 8.0 或更新版本) 。|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE` if 函式只在 DIA SDK 8.0 或更新版本) 中標示為靜態 (。|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|封閉函數的符號。|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|詞彙父符號的識別碼。|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|起點具有靜態位置;如需詳細資訊，請參閱 [符號位置](../../debugger/debug-interface-access/symbol-locations.md)。|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` 如果函式是使用 [noinline](https://msdn.microsoft.com/library/f259d55b-dec7-4bde-8cf9-14521e4fdc42) 屬性指定， (只有 DIA SDK 8.0 或更新版本) 。|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` 如果函式是使用 [noreturn](https://msdn.microsoft.com/library/9c6517e5-22d7-4051-9974-3d2200ae4d1d) 屬性指定， (只有 DIA SDK 8.0 或更新版本) 。|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` 如果函式永遠不會被呼叫 (只有 DIA SDK 8.0 或更新版本) 。|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|記憶體中符號的位移;如需詳細資訊，請參閱 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md) `LocIsRegRel` 。|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` 如果程式碼只有 DIA SDK 8.0 或更新版本) 中的優化程式碼的 debug 資訊 (。|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|函數在其區塊內的相對位置。|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|傳回 `SymTagFuncDebugStart` (其中一個) 的 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md) 值。|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|函數在可執行檔中的位置。|  
  
## <a name="see-also"></a>另請參閱  
 [符號類型的詞法階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)   
 [符號位置](../../debugger/debug-interface-access/symbol-locations.md)
