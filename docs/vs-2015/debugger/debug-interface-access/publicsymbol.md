---
title: PublicSymbol |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- data symbols [C++]
- PublicSymbol symbol
- global functions [C++], as public symbols
ms.assetid: f8d33007-302d-4549-9dad-47fb33ea60b7
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8f36480dc8ddaac3d9977155f2b1a7741ebe3ba1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155595"
---
# <a name="publicsymbol"></a>PublicSymbol
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

建立 .exe 檔案時，每個公用符號最少 (，每個全域函式和資料符號) 都會獲得一個 `SymTagPublicSymbol` 標記。  
  
## <a name="properties"></a>屬性  
 下表顯示對此符號類型有效的屬性。  
  
|屬性|資料類型|描述|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Location 的位移部分;如需詳細資訊，請參閱 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Location 的部分;如需詳細資訊，請參閱 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)。|  
|[IDiaSymbol::get_code](../../debugger/debug-interface-access/idiasymbol-get-code.md)|`BOOL`|`TRUE` 如果符號的位置是在程式碼中，則為。|  
|[IDiaSymbol::get_function](../../debugger/debug-interface-access/idiasymbol-get-function.md)|`BOOL`|`TRUE` 如果符號為函數，則為。|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|此符號的長度（以位元組為單位）。|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|全域範圍的符號。|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|詞彙父符號的識別碼。|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|公用符號具有靜態位置;如需詳細資訊，請參閱 [符號位置](../../debugger/debug-interface-access/symbol-locations.md)。|  
|[IDiaSymbol::get_managed](../../debugger/debug-interface-access/idiasymbol-get-managed.md)|`BOOL`|`TRUE` 如果符號的位置在 managed 程式碼中，則為。|  
|[IDiaSymbol::get_msil](../../debugger/debug-interface-access/idiasymbol-get-msil.md)|`BOOL`|`TRUE` 如果符號的位置是 Microsoft 中繼語言 (MSIL) 程式碼。|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|符號的完整裝飾名稱。|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|符號在其區塊內的相對位置。|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|傳回 `SymTagPublicSymbol` (其中一個) 的 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md) 值。|  
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|`BSTR`|未修飾的符號名稱。|  
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|`BSTR`|部分或所有未修飾的符號名稱。|  
  
## <a name="see-also"></a>另請參閱  
 [符號類型的詞法階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)   
 [符號位置](../../debugger/debug-interface-access/symbol-locations.md)
