---
title: IDiaSymbol::get_hasSEH | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSEH method
ms.assetid: 1a709ded-22c8-464c-97be-eba5e464210c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0689490e855508314835a21e44e6cb9a02736ef4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863302"
---
# <a name="idiasymbolget_hasseh"></a>IDiaSymbol::get_hasSEH
抓取旗標，這個旗標會指定函數是否包含任何 [結構化例外狀況處理 (C/c + +) ](/cpp/cpp/structured-exception-handling-c-cpp) (例如 __try/ \_ _except 區塊) 。

## <a name="syntax"></a>語法

```C++
HRESULT get_hasSEH(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>參數
 `pFlag`

擴展如果函式 `TRUE` 具有任何結構化例外狀況處理區塊，則傳回，否則傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
 如果成功， `S_OK` 則傳回; 否則傳回 `S_FALSE` 錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。

## <a name="requirements"></a>規格需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本：|DIA SDK v8.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Structured Exception Handling (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp)