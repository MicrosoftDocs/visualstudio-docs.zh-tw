---
title: IDiaEnumSegments::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Next method
ms.assetid: 53f61874-d821-47ab-a1f5-27e982804a6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34062b654cbaccec053c5ac50bfb041d37a0f4e6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744196"
---
# <a name="idiaenumsegmentsnext"></a>IDiaEnumSegments::Next
抓取列舉序列中指定數目的區段。

## <a name="syntax"></a>語法

```C++
HRESULT Next ( 
   ULONG         celt,
   IDiaSegment** rgelt,
   ULONG*        pceltFetched
);
```

#### <a name="parameters"></a>參數
 celt

在列舉值中要抓取的區段數目。

 rgelt

脫銷要填入的陣列，其中包含代表區段的所需[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)物件。

 pceltFetched

脫銷傳回已提取列舉值中的區段數目。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 如果沒有其他區段，則傳回 `S_FALSE`。 否則會傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)