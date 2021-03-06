---
description: 此函式會抓取旗標，這個旗標會指出是否無法在堆疊緩衝區檢查 ([/gs (緩衝區安全性檢查) ](/cpp/build/reference/gs-buffer-security-check) 編譯器選項) 中完成堆疊排序。
title: IDiaSymbol：： get_noStackOrdering |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_noStackOrdering method
ms.assetid: a1753917-705b-4165-9880-d05e91e6dcb4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fbfcb8c4404179431c4c480ee036210cb2d0be77
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147156"
---
# <a name="idiasymbolget_nostackordering"></a>IDiaSymbol::get_noStackOrdering
此函式會抓取旗標，這個旗標會指出是否無法在堆疊緩衝區檢查 ([/gs (緩衝區安全性檢查) ](/cpp/build/reference/gs-buffer-security-check) 編譯器選項) 中完成堆疊排序。

## <a name="syntax"></a>語法

```C++
HRESULT get_noStackOrdering(
   BOOL *pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展 `TRUE` 如果無法在堆疊緩衝區檢查過程中完成堆疊排序，則傳回，否則傳回 `FALSE` 。

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
- [/GS (緩衝區安全性檢查) ](/cpp/build/reference/gs-buffer-security-check)
