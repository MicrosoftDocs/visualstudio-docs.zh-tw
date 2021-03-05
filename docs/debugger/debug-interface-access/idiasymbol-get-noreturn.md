---
description: 抓取旗標，這個旗標會指定函式是否已標示為永遠不會以 noreturn) 屬性來傳回。
title: IDiaSymbol：： get_noReturn |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_noReturn method
ms.assetid: 704c1cc0-5b84-4334-a02a-70f43aff39d5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6d3d140afd80855be7afeeef11481d5df20c057b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147181"
---
# <a name="idiasymbolget_noreturn"></a>IDiaSymbol::get_noReturn
抓取旗標，這個旗標會指定函式是否已標示為永遠不會以 [noreturn](/cpp/cpp/noreturn) 屬性傳回。

## <a name="syntax"></a>語法

```C++
HRESULT get_noReturn(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>參數
 pFlag

擴展如果函式已宣告 `TRUE` 為從未以屬性傳回，則傳回 `noreturn` ，否則傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。

## <a name="requirements"></a>規格需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本：|DIA SDK v8.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [noreturn](/cpp/cpp/noreturn)
