---
title: IDiaSegment::get_execute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_execute method
ms.assetid: 746cdf8e-9097-415d-ba10-069854153185
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 349b9b865223e2df0083e12d4c8bfd26ae2c2643
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466004"
---
# <a name="idiasegmentget_execute"></a>IDiaSegment::get_execute
抓取表示區段是否為可執行檔的旗標。

## <a name="syntax"></a>語法

```C++
HRESULT get_execute ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷`TRUE`如果區段標示為可執行，則傳回，否則會傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援此屬性，則傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)