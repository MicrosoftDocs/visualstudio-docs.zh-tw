---
description: 抓取旗標，這個旗標會指定函式是否包含對 alloca (的呼叫，此呼叫是用來配置堆疊) 的記憶體。
title: IDiaSymbol::get_hasAlloca | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasAlloca method
ms.assetid: 3b9fb747-670b-4da7-bb70-612f7b911786
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 42b2c63932cc37e0c5c605e31e9dfb0671fdd586
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160999"
---
# <a name="idiasymbolget_hasalloca"></a>IDiaSymbol::get_hasAlloca
抓取旗標，這個旗標會指定函式是否包含 (的呼叫，該呼叫 `alloca` 用來配置堆疊) 的記憶體。

## <a name="syntax"></a>語法

```cpp
HRESULT get_hasAlloca(   BOOL *pFlag);
```

#### <a name="parameters"></a>參數
 `pFlag`

擴展 `TRUE` 如果函數包含的呼叫，則傳回 `alloca` ，否則傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該屬性不適用於符號。

## <a name="requirements"></a>規格需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本：|DIA SDK v8.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
