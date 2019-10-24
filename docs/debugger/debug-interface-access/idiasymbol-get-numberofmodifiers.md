---
title: IDiaSymbol：： get_numberOfModifiers |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 61ff7431-1994-4f7e-a182-1817f16f60a9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e034f081f8a279a65134c40e5ee485cd1d08d9b3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739676"
---
# <a name="idiasymbolget_numberofmodifiers"></a>IDiaSymbol::get_numberOfModifiers
抓取套用至原始類型的修飾詞數目。

## <a name="syntax"></a>語法

```C++
HRESULT get_numberOfModifiers(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷@No__t_0 的指標，指定套用至原始類型的修飾詞數目。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)