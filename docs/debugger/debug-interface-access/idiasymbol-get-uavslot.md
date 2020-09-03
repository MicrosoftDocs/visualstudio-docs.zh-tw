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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85461655"
---
# <a name="idiasymbolget_uavslot"></a>IDiaSymbol::get_uavSlot
抓取 uav 插槽。

## <a name="syntax"></a>語法

```C++
HRESULT get_uavSlot(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展保存 uav 位置之的指標 `DWORD` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)