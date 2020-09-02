---
title: IDiaEnumSegments::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: e03c01efb9f2dca13009a7dc7eeb8282b5c9082c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468041"
---
# <a name="idiaenumsegmentsitem"></a>IDiaEnumSegments::Item
藉由索引來抓取區段。

## <a name="syntax"></a>語法

```C++
HRESULT Item ( 
   DWORD         index,
   IDiaSegment** segment
);
```

#### <a name="parameters"></a>參數
 索引

在要抓取之 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) 物件的索引。 索引位於0到-1 的範圍內 `count` ，其中 `count` 是 [IDiaEnumSegments：： get_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md) 方法所傳回的。

 segment

擴展傳回代表所需區段的 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)