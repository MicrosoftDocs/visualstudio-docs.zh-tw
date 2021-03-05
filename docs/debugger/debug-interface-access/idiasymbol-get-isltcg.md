---
description: 抓取旗標，這個旗標會指定編譯單位) 是否已連結至連結器參數/LTCG (連結時產生程式碼)  (/cpp/build/reference/ltcg-link-time-code-generation) ，以協助整個程式優化。
title: IDiaSymbol::get_isLTCG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isLTCG method
ms.assetid: 5f7f05b8-6b71-4958-9e1e-e4924ef9c59b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1b8306dabe6533287d7d28841ea76f2d6478e4a3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160810"
---
# <a name="idiasymbolget_isltcg"></a>IDiaSymbol::get_isLTCG
抓取旗標，這個旗標會指定 [編譯單位](../../debugger/debug-interface-access/compiland.md) 是否已連結至連結器切換 [/ltcg (連結時產生程式碼) ](/cpp/build/reference/ltcg-link-time-code-generation)，以協助整個程式優化。 此參數只適用于 managed 程式碼。

## <a name="syntax"></a>語法

```C++
HRESULT get_iSLTCG(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>參數
 pFlag

擴展 `TRUE` 如果 `compiland` 已與/ltcg 連結器參數連結，則傳回，否則傳回 `FALSE` 。

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
