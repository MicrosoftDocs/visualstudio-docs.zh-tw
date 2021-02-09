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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1a4533b34b35f5050e3bb13a9dee9c74fa69c61d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856349"
---
# <a name="idiaenumsegmentsnext"></a>IDiaEnumSegments::Next
捕獲列舉序列中指定的區段數目。

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

在要抓取之列舉值中的區段數目。

 rgelt

擴展要填入代表區段之所需 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) 物件的陣列。

 pceltFetched

擴展傳回已提取列舉值中的區段數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果沒有其他區段，則會傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)