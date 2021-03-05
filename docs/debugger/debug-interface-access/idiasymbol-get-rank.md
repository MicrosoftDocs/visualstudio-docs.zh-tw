---
description: 抓取 FORTRAN 多維陣列的維度)  (數目排名。
title: IDiaSymbol：： get_rank |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_rank method
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4da2bb7dc41d06e113e0bd278ef08917771cfb2e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161911"
---
# <a name="idiasymbolget_rank"></a>IDiaSymbol::get_rank
抓取 FORTRAN 多維陣列的維度)  (數目排名。

## <a name="syntax"></a>語法

```C++
HRESULT get_rank ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展傳回 FORTRAN 多維度陣列中的維度數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。

## <a name="remarks"></a>備註
 Rank 指的是陣列中陣列宣告為的維度數目 `myarray[1,2,3]` 。 此範例的等級為3和3個維度。 Rank 不適用於 c + +，它會針對每個維度使用陣列陣列的概念 (也就是 `myarray[1][2][3]`) 。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
