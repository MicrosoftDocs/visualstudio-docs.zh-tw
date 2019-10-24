---
title: IDiaEnumSegments::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Item method
ms.assetid: ee44dd55-39a0-4b7b-97ff-2e1226eeb2bd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 101821e3c00d3aeac9b131ee5a11ab9a01e090a9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744175"
---
# <a name="idiaenumsegmentsitem"></a>IDiaEnumSegments::Item
透過索引來抓取區段。

## <a name="syntax"></a>語法

```C++
HRESULT Item ( 
   DWORD         index,
   IDiaSegment** segment
);
```

#### <a name="parameters"></a>參數
 索引

在要抓取的[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)物件索引。 索引的範圍是0到 `count`-1，其中 `count` 是由[IDiaEnumSegments：： get_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md)方法傳回。

 segment

脫銷傳回[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)物件，代表所需的區段。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)