---
title: IDiaSymbol：： get_uavSlot |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: a70648f2-3b25-439f-8099-239ac602515a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c0d4afea1525a52453d83b804cfb06a95bce932c
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461655"
---
# <a name="idiasymbolget_uavslot"></a>IDiaSymbol::get_uavSlot
抓取 uav 位置。

## <a name="syntax"></a>語法

```C++
HRESULT get_uavSlot(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷包含 uav 位置之的指標 `DWORD` 。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)