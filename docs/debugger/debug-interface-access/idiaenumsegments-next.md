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
ms.openlocfilehash: f9b0f0d06ae5303277c296fd56e36e60b9a6f022
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56624603"
---
# <a name="idiaenumsegmentsnext"></a>IDiaEnumSegments::Next
擷取指定的數目的列舉型別序列中的區段。

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

[in]要擷取列舉值中的區段數目。

 rgelt

[out]陣列，是要與需要填入[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)表示區段的物件。

 pceltFetched

[out]擷取列舉值中傳回區段的數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 傳回`S_FALSE`如果有沒有更多區段。 否則會傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)