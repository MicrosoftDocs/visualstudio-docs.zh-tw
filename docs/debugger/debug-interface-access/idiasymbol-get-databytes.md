---
title: IDiaSymbol：： get_dataBytes |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_dataBytes method
ms.assetid: 5eb37179-20d8-44ae-a72a-405c1b0435c4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 203732d2ac222f4b4b74fa2e4c90f05b05754b47
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463957"
---
# <a name="idiasymbolget_databytes"></a>IDiaSymbol::get_dataBytes
抓取 OEM 符號的資料位元組。

## <a name="syntax"></a>語法

```C++
HRESULT get_dataBytes ( 
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>參數
 `cbData`

在用來保存資料的緩衝區大小。

 `pcbData`

脫銷傳回寫入的位元組數目，或者，如果 `data` 參數為，則傳回 `NULL` 可用的位元組數目。

 `data[]`
- [out，]以資料位元組填滿的緩衝區。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該屬性不適用於符號。

## <a name="requirements"></a>需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本：|DIA SDK v7.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)