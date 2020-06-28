---
title: IDiaSymbol::get_oemSymbolId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_oemSymbolId method
ms.assetid: 187801f0-bd82-4c5b-9fae-8eeb1a4ac0ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 401894a921f2ad6a9649e337059c8ee142858f84
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85462620"
---
# <a name="idiasymbolget_oemsymbolid"></a>IDiaSymbol::get_oemSymbolId
抓取原始設備製造商（OEM）符號的識別碼值。

## <a name="syntax"></a>語法

```C++
HRESULT get_oemSymbolId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回 OEM 內部指派的符號識別碼。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示此屬性無法用於符號。

## <a name="remarks"></a>備註
 識別碼是 DIA SDK 所建立的唯一值，用來將所有符號標記為唯一。

 這個屬性只適用于[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)類型為的符號 `SymTagCustomType` 。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)