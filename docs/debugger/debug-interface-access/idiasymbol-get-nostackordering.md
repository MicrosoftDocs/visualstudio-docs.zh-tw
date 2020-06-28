---
title: IDiaSymbol：： get_noStackOrdering |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_noStackOrdering method
ms.assetid: a1753917-705b-4165-9880-d05e91e6dcb4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c82b8c4836d97f02fa84aec500d961911f993df3
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85462788"
---
# <a name="idiasymbolget_nostackordering"></a>IDiaSymbol::get_noStackOrdering
此函式會抓取一個旗標，指出是否無法在堆疊緩衝區檢查（[/gs （緩衝區安全性檢查）](/cpp/build/reference/gs-buffer-security-check)編譯器選項）中執行堆疊排序。

## <a name="syntax"></a>語法

```C++
HRESULT get_noStackOrdering(
   BOOL *pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷`TRUE`如果無法在堆疊緩衝區檢查過程中完成堆疊排序，則傳回，否則傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該屬性不適用於符號。

## <a name="requirements"></a>需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本：|DIA SDK v8.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [/GS （緩衝區安全性檢查）](/cpp/build/reference/gs-buffer-security-check)