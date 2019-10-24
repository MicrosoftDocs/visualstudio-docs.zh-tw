---
title: IDiaSymbol：： get_container |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_container method
ms.assetid: 24e832eb-80b3-484c-a41b-11477ec9de99
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0533eb2cdea1dd3e1bea3d64e2b94ce29a09353d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740769"
---
# <a name="idiasymbolget_container"></a>IDiaSymbol::get_container
此函式會抓取符號的指標，代表這個符號的父系/容器。

## <a name="syntax"></a>語法

```C++
HRESULT get_container(
   IDiaSymbol **pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回 `IDiaSymbol` 的指標，其中包含此符號之容器的相關資訊。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK;否則，會傳回 S_FALSE 或錯誤碼。

> [!NOTE]
> 傳回值為 S_FALSE 表示此屬性無法用於符號。

## <a name="requirements"></a>需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本:|DIA SDK v8.0|

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)