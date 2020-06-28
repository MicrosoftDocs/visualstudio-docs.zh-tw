---
title: ManagedType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- SymTagManagedType symbol
- managed type symbol
- ManagedType symbol
ms.assetid: 5db99e2a-4f2e-4796-89b7-b401b151826f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c53bcac98629d2dfbd1537ff4486b0a0162b4d9d
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461186"
---
# <a name="managedtype"></a>ManagedType
受控型別（中繼資料所定義的任何符號，或 c # 等語言的記憶體和資源管理功能的原生）都是以符號來識別 `SymTagManagedType` 。

## <a name="properties"></a>屬性
 下表顯示此符號類型的其他有效屬性。

|屬性|資料類型|描述|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Managed 符號的名稱。|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|符號的索引識別碼。|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|傳回 `SymTagManagedType` （其中一個[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)值）。|

## <a name="see-also"></a>另請參閱
- [符號類型的類別階層架構](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)