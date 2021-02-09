---
title: BaseType | Microsoft Docs
description: 在 Visual Studio debug interface access SDK 中尋找有關 BaseType 符號類型 (SymTagBaseType) 的參考資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BaseType symbol [DIA SDK]
ms.assetid: 2f9e22e6-8360-496a-ac6b-17a5a56b0c46
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 38ef0b8d8172bfba915da752526098144c2e40b2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857474"
---
# <a name="basetype"></a>BaseType
基底類型是以 `SymTagBaseType` 符號來識別。

## <a name="properties"></a>屬性
 下表顯示此符號類型的其他有效屬性。

|屬性|資料類型|描述|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|`DWORD`|[BasicType 列舉](../../debugger/debug-interface-access/basictype.md)的其中一個值。|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` 如果基底類型標示為 const。|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`LONGLONG`|基底類型的大小（以位元組為單位）。|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|封閉 [編譯單位](../../debugger/debug-interface-access/compiland.md)的符號。|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|詞彙父符號的識別碼。|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|傳回 `SymTagBaseType` (其中一個) 的 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md) 值。|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` 如果基底類型為未對齊。|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` 如果基底類型標示為 volatile。|

## <a name="see-also"></a>另請參閱
- [BasicType 列舉](../../debugger/debug-interface-access/basictype.md)
- [符號類型的類別階層架構](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)