---
description: 抓取旗標，這個旗標會指定函式是否具有 naked) 屬性 (也就是說，函式沒有編譯器) 所新增的初構或終解程式碼。
title: IDiaSymbol：： get_isNaked |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isNaked method
ms.assetid: b16629dc-8e17-476b-9c7b-58e7277c61ed
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6ec1d273ce826a87ae658f7ed22fe7680edad25d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156157"
---
# <a name="idiasymbolget_isnaked"></a>IDiaSymbol::get_isNaked
抓取旗標，這個旗標會指定函式是否具有 [naked](/cpp/cpp/naked-cpp) 屬性 (也就是說，函式沒有編譯器) 所新增的初構或終解程式碼。

## <a name="syntax"></a>語法

```C++
HRESULT get_isNaked(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>參數
 `pFlag`

擴展 `TRUE` 如果函數具有屬性，則傳回 `naked` ，否則傳回 `FALSE` 。

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
- [Naked 函式呼叫](/cpp/cpp/naked-function-calls)
