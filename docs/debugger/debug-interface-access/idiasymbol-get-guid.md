---
title: IDiaSymbol：： get_guid |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_guid method
ms.assetid: c02a6c92-f406-4646-82e7-3cd005af900e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 27c672f3738585923348ac5c36df681b4de60ca7
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463817"
---
# <a name="idiasymbolget_guid"></a>IDiaSymbol::get_guid
抓取符號的全域唯一識別碼（GUID）。

## <a name="syntax"></a>語法

```C++
HRESULT get_guid ( 
   GUID* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回符號的 GUID。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示此屬性無法用於符號。

## <a name="requirements"></a>需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本：|DIA SDK v7.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)