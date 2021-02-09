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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d7c63c9464b0d8c716b4946dab5c5b86d198a14c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853671"
---
# <a name="idiasymbolget_registerid"></a>IDiaSymbol::get_registerId
當 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md) 設定為時，抓取位置的註冊指示項 `LocIsEnregistered` 。

## <a name="syntax"></a>語法

```C++
HRESULT get_registerId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展傳回位置的註冊指示項。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該屬性不適用於符號。

## <a name="remarks"></a>備註
 如果符號是相對於暫存器，亦即，如果符號的 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md) 設定為 `LocIsRegRel` ，請使用 `get_registerId` 方法，然後呼叫 [IDiaSymbol：： get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) 方法，以取得符號所在位置之暫存器的位移。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)