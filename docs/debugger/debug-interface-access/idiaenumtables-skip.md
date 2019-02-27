---
title: IDiaEnumTables::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Skip method
ms.assetid: 5c9db956-0654-4f1a-8775-530aa980d8ec
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24232878452082dd1769c9bc9f1cd22d081968f2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596551"
---
# <a name="idiaenumtablesskip"></a>IDiaEnumTables::Skip
略過指定的數目的列舉型別序列中的資料表。

## <a name="syntax"></a>語法

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>參數
 `celt`

[in]略過列舉序列中的資料表數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`有沒有更多的資料表，以略過。

## <a name="see-also"></a>請參閱
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)