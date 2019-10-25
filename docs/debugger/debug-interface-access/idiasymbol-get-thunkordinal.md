---
title: IDiaSymbol::get_thunkOrdinal | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3bc8c523886d694ea413dedcf9a28e53e361882b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739143"
---
# <a name="idiasymbolget_thunkordinal"></a>IDiaSymbol::get_thunkOrdinal
捕獲函數的 Thunk 類型。

## <a name="syntax"></a>語法

```C++
HRESULT get_thunkOrdinal ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回[THUNK_ORDINAL 列舉](../../debugger/debug-interface-access/thunk-ordinal.md)列舉中的值，指定函式的 THUNK 類型。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。

> [!NOTE]
> `S_FALSE` 的傳回值表示該屬性不適用於符號。

## <a name="remarks"></a>備註
 只有當符號做為 `SymTagThunk` 的[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)值時，這個屬性才有效。

 「Thunk」是一段程式碼，可在32位記憶體位址空間（也稱為一般位址空間）和16位位址空間（稱為分段位址空間）之間進行轉換。

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [THUNK_ORDINAL 列舉](../../debugger/debug-interface-access/thunk-ordinal.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)