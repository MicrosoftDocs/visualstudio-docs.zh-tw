---
description: 藉由索引來抓取區段。
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a8714964bdf2e267e9f9c047fb1878655e58f489
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148847"
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
