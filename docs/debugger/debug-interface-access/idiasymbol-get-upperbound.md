---
title: IDiaSymbol：： get_upperBound |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_upperBound method
ms.assetid: a77dcafa-ea3f-45da-826d-8f9b4489a03f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b34f8e807a6aad5acc9ac07e6805d0faf488de3
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461550"
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

脫銷傳回代表 FORTRAN 陣列維度上限的[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示此屬性無法用於符號。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)