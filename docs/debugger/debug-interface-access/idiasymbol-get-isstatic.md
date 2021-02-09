---
title: IDiaSymbol：： get_isStatic |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isStatic method
ms.assetid: 3be5fe1b-46e8-4b07-90d8-4929dbbe7ff7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 338c2e650b59f501bbf184e877ca1e1f08b924c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863106"
---
# <a name="idiasymbolget_isstatic"></a>IDiaSymbol::get_isStatic
抓取旗標，這個旗標會指定函式或 Thunk 圖層是否已標示為靜態。

## <a name="syntax"></a>語法

```C++
HRESULT get_isStatic(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>參數
 `pFlag`

擴展 `TRUE` 如果函數或 Thunk 層已標示為靜態，則傳回，否則傳回 `FALSE` 。

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