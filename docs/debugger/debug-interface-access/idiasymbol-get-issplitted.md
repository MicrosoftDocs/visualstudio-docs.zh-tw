---
description: 抓取旗標，這個旗標會指定資料符號是否已分割成其他符號的匯總或集合;編譯器會將符號視為個別的實體，即使它們真的是較大符號的一部分也是一樣。
title: IDiaSymbol：： get_isSplitted |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isSplitted method
ms.assetid: ff160cf6-003b-4ef5-a406-20a7b287b2bf
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5dd9807928ca5f1b8d2e3b20c5de3ec30adc70db
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162051"
---
# <a name="idiasymbolget_issplitted"></a>IDiaSymbol::get_isSplitted
抓取旗標，這個旗標會指定資料符號是否已分割成其他符號的匯總或集合;編譯器會將符號視為個別的實體，即使它們真的是較大符號的一部分也是一樣。

## <a name="syntax"></a>語法

```C++
HRESULT get_isSplitted(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>參數
 `pFlag`

擴展 `TRUE` 如果符號已分割成符號的匯總，則傳回，否則傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
 如果成功， `S_OK` 則傳回; 否則傳回 `S_FALSE` 錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。

## <a name="remarks"></a>備註
 [IDiaSymbol：： get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)方法 `TRUE` 會針對屬於分割符號一部分的所有符號傳回。

## <a name="requirements"></a>規格需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本：|DIA SDK v8.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)
