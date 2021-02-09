---
title: IDiaSymbol：： get_liveRangeLength |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeLength
ms.assetid: ffcce3cc-085c-44eb-8145-46e3819c54f9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b243159cccc53361e833107fdf4d6381833ac6da
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863015"
---
# <a name="idiasymbolget_liverangelength"></a>IDiaSymbol::get_liveRangeLength
傳回區域符號有效的位址範圍長度。

## <a name="syntax"></a>語法

```C++
HRESULT get_liveRangeLength ( 
   ULONGLONG* length
);
```

#### <a name="parameters"></a>參數
 `length`

擴展傳回位址範圍的長度。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

> [!NOTE]
> 傳回的錯誤碼表示符號沒有即時範圍資訊。

## <a name="remarks"></a>備註

## <a name="requirements"></a>需求
 標頭： Dia2。h

 程式庫： diaguids .lib

 DLL： msdia100.dll

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)