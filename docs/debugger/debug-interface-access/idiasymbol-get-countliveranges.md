---
title: IDiaSymbol：： get_countLiveRanges |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_countLiveRanges
ms.assetid: 55f79e1a-d4c2-42cd-ab37-d8253b20e34c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 990673afdb01b1471ad75d65036610c486e735c4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740749"
---
# <a name="idiasymbolget_countliveranges"></a>IDiaSymbol::get_countLiveRanges
抓取與本機符號相關聯的有效位址範圍數目。

## <a name="syntax"></a>語法

```C++
HRESULT get_countLiveRanges ( 
   DWORD* count
);
```

#### <a name="parameters"></a>參數
 `count`

脫銷傳回位址範圍的數目。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。

## <a name="requirements"></a>需求
 標頭： Dia2。h

 程式庫： diaguids

 DLL： msdia100

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)