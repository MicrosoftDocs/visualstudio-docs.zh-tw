---
title: IDiaSymbol：： get_hasAssignmentOperator |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasAssignmentOperator method
ms.assetid: fb1acb9c-4500-4343-a590-0395789e4040
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce2da67192ed5ab3bea2f24c2ed52a7655ff1f8e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740583"
---
# <a name="idiasymbolget_hasassignmentoperator"></a>IDiaSymbol::get_hasAssignmentOperator
抓取指定使用者定義資料類型是否已定義任何指派運算子的旗標。

## <a name="syntax"></a>語法

```C++
HRESULT get_hasAssignmentOperator ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷如果使用者定義資料類型已定義任何指派運算子，則傳回 `TRUE`;否則，會傳回 `FALSE`。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。

> [!NOTE]
> @No__t_0 的傳回值表示該屬性不適用於符號。

## <a name="requirements"></a>需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本:|DIA SDK v7.0|

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)