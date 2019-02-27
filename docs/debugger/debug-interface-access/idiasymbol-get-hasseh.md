---
title: IDiaSymbol::get_hasSEH | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSEH method
ms.assetid: 1a709ded-22c8-464c-97be-eba5e464210c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bf5d6f31d25d72cd6bc71f9d8b17443b3d8fc8a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56643726"
---
# <a name="idiasymbolgethasseh"></a>IDiaSymbol::get_hasSEH
擷取指定的函式是否包含任何的旗標[Structured Exception Handling （C/c + +）](/cpp/cpp/structured-exception-handling-c-cpp) (例如 __try /\__except 區塊)。

## <a name="syntax"></a>語法

```C++
HRESULT get_hasSEH(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>參數
 `pFlag`

[out]會傳回`TRUE`函式有任何結構化的例外狀況處理區塊; 否則會傳回`FALSE`。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。

> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於符號。

## <a name="requirements"></a>需求

|需求|說明|
|-----------------|-----------------|
|標頭：|dia2.h|
|版本:|DIA SDK v8.0|

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [結構化例外狀況處理 (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp)