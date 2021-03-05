---
description: 抓取代表 FORTRAN 陣列維度上限的符號。
title: IDiaSymbol：： get_upperBound |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_upperBound method
ms.assetid: a77dcafa-ea3f-45da-826d-8f9b4489a03f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8e07eed5400b49adc38bff878207cf4d9f38eada
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161778"
---
# <a name="idiasymbolget_upperbound"></a>IDiaSymbol::get_upperBound
抓取代表 FORTRAN 陣列維度上限的符號。

## <a name="syntax"></a>語法

```C++
HRESULT get_upperBound ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展傳回 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 物件，這個物件表示 FORTRAN 陣列維度的上限。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
