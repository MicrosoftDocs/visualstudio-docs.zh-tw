---
title: IDiaSegment::get_write | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_write method
ms.assetid: 5fcda988-6be1-4b2f-8660-b59aa78fc35d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 498a72888ff59d09abf4f8d4dd830db25678761c
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465934"
---
# <a name="idiasegmentget_write"></a>IDiaSegment::get_write
抓取指出是否可以修改區段的旗標。

## <a name="syntax"></a>語法

```C++
HRESULT get_write ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷`TRUE`如果區段可以寫入，則傳回，否則傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援此屬性，則傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)