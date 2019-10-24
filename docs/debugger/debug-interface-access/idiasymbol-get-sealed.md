---
title: IDiaSymbol：： get_sealed |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_sealed method
ms.assetid: cd1fef1f-47de-47c7-885f-f6f0a9a07d8c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ece720a42b606640d02729951c11ae03d092aedf
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739353"
---
# <a name="idiasymbolget_sealed"></a>IDiaSymbol::get_sealed
抓取指定類別或方法是否為密封的旗標。

## <a name="syntax"></a>語法

```C++
HRESULT get_sealed( 
   BOOL* pRetVal)
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷如果類別或方法已密封，則傳回 `TRUE`。否則，會傳回 `FALSE`。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。

> [!NOTE]
> @No__t_0 的傳回值表示該屬性不適用於符號。

## <a name="remarks"></a>備註
 密封類別不能當做基底類別使用。 密封的方法無法覆寫。

## <a name="requirements"></a>需求
 標頭： Dia2。h

 程式庫： diaguids

 DLL： msdia100

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)