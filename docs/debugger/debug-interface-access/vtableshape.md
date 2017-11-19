---
title: "VTableShape |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- VTableShape symbol
- SymTagVTableShape tag
ms.assetid: dd97f4c3-115d-46a9-b506-2531e30a0d8f
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d0a1e45e4c3efaf91250e5ebf557c218051adb1a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="vtableshape"></a>VTableShape
[VTable](../../debugger/debug-interface-access/vtable.md)符號有所識別的類別子符號`SymTagVTableShape`標記。  
  
## <a name="properties"></a>屬性  
 下表顯示這個符號類型的其他有效屬性。  
  
|屬性|資料類型|說明|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE`如果類別的 VTable 標示為常數。|  
|[IDiaSymbol::get_count](../../debugger/debug-interface-access/idiasymbol-get-count.md)|`DWORD`|在 VTable 中的項目數。|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|封入編譯模組的符號。|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|語彙父符號的識別碼。|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|傳回`SymTagVTableShape`(其中[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)值)。|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE`如果在 VTable 的類別是未對齊。|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE`如果類別的 VTable 標示為 volatile。|  
  
## <a name="see-also"></a>另請參閱  
 [符號類型的類別階層架構](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [VTable](../../debugger/debug-interface-access/vtable.md)