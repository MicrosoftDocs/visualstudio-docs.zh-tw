---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 009fcf437f56852e324e392f6a5691dd23e23ebc
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463362"
---
# <a name="idiasymbolget_isltcg"></a>IDiaSymbol::get_isLTCG
抓取旗標，指定[編譯模組](../../debugger/debug-interface-access/compiland.md)是否已與連結器參數[/ltcg （連結時間程式碼產生）](/cpp/build/reference/ltcg-link-time-code-generation)連結，以協助整個程式優化。 此參數只適用于 managed 程式碼。

## <a name="syntax"></a>語法

```C++
HRESULT get_iSLTCG(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>參數
 pFlag

脫銷`TRUE`如果 `compiland` 是使用/ltcg 連結器參數所連結，則會傳回，否則會傳回 `FALSE` 。

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