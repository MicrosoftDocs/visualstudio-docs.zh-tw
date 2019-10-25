---
title: IDiaSymbol::get_registerId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ffd349b56c4292de04d5d7a38e82eeafed6775e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739456"
---
# <a name="idiasymbolget_registerid"></a>IDiaSymbol::get_registerId
當[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)設定為 `LocIsEnregistered` 時，抓取位置的 register 指示項。

## <a name="syntax"></a>語法

```C++
HRESULT get_registerId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回位置的 register 指示項。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。

> [!NOTE]
> @No__t_0 的傳回值表示該屬性不適用於符號。

## <a name="remarks"></a>備註
 如果符號相對於暫存器，也就是，如果符號的[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)設定為 `LocIsRegRel`，請使用 `get_registerId` 方法，然後呼叫[IDiaSymbol：： get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)方法，以取得暫存器中符號所在位置的位移後面.

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)