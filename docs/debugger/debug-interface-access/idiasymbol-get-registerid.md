---
title: IDiaSymbol::get_registerId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: f252d02a137ada627c0c546e1f1ac79118f76de9
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85462473"
---
# <a name="idiasymbolget_registerid"></a>IDiaSymbol::get_registerId
當[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)設定為時，抓取位置的 register 指示項 `LocIsEnregistered` 。

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
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該屬性不適用於符號。

## <a name="remarks"></a>備註
 如果符號是相對於暫存器，也就是，如果符號的[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)設定為 `LocIsRegRel` ，請使用方法， `get_registerId` 然後再呼叫[IDiaSymbol：： get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)方法，以從符號所在的暫存器取得位移。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)