---
title: IDiaSymbol::get_editAndContinueEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_editAndContinueEnabled method
ms.assetid: cd703c64-9ff8-4654-8493-8cde9309cb22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2dd1d3c7cefe76feec5c65176450d0e73a77a25
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740703"
---
# <a name="idiasymbolget_editandcontinueenabled"></a>IDiaSymbol::get_editAndContinueEnabled
抓取表示模組是否使用[/Z7、/zi、/zi （Debug 資訊格式）](/cpp/build/reference/z7-zi-zi-debug-information-format)編譯器參數編譯的旗標。

## <a name="syntax"></a>語法

```C++
HRESULT get_editAndContinueEnabled ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷如果在編譯時啟用了 [編輯後繼續]，則會傳回 `TRUE`;否則，會傳回 `FALSE`。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。

> [!NOTE]
> @No__t_0 的傳回值表示該屬性不適用於符號。

## <a name="requirements"></a>需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本:|DIA SDK v7.0|

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [/Z7、/Zi、/ZI (偵錯資訊格式)](/cpp/build/reference/z7-zi-zi-debug-information-format)