---
description: 捕獲函式的 Thunk 型別。
title: IDiaSymbol::get_thunkOrdinal | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: de9b0fa692ff44096e962bc952b91c3f2fd314f2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160607"
---
# <a name="idiasymbolget_thunkordinal"></a>IDiaSymbol::get_thunkOrdinal
捕獲函式的 Thunk 型別。

## <a name="syntax"></a>語法

```C++
HRESULT get_thunkOrdinal ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展傳回 [THUNK_ORDINAL 列舉](../../debugger/debug-interface-access/thunk-ordinal.md) 列舉中的值，這個值會指定函數的 THUNK 型別。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。

## <a name="remarks"></a>備註
 只有當符號做為的 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md) 值時，這個屬性才有效 `SymTagThunk` 。

 「Thunk」是一段程式碼，可在32位的記憶體位址空間之間進行轉換， (也稱為一般位址空間) 和16位位址空間 (稱為分割的位址空間) 。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [THUNK_ORDINAL 列舉](../../debugger/debug-interface-access/thunk-ordinal.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)
