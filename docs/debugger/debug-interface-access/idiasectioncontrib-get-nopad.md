---
title: IDiaSectionContrib::get_nopad | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_nopad method
ms.assetid: f5c08603-0b3e-4e81-acf1-1b95a6a83bed
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a81113242379070e56d6d0bd0f916355985eaa42
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742616"
---
# <a name="idiasectioncontribget_nopad"></a>IDiaSectionContrib::get_nopad
抓取表示區段是否不應填補至下一個記憶體界限的旗標。

## <a name="syntax"></a>語法

```C++
HRESULT get_nopad(
   BOOL* pRetVal
};
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷如果區段不應填補至下一個記憶體界限，則傳回 `TRUE`。否則會傳回 `FALSE`。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 如果不支援此屬性，則傳回 `S_FALSE`。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 此屬性通常只會出現在較舊的檔案上。

## <a name="see-also"></a>請參閱
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)