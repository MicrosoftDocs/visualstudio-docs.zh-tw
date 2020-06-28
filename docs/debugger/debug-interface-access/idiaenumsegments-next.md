---
title: IDiaEnumSegments::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: f8e87efa1ed616a38ccb79fec1e286417c10124b
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468027"
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
 如果成功，則傳回 `S_OK`。 如果沒有其他區段，則傳回 `S_FALSE` 。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)