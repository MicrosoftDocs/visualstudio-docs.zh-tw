---
title: IDiaEnumFrameData：： Next |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Next method
ms.assetid: 546e2e23-efb2-425a-96a1-808c67c519fb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6fe478e503ed6e16ee570f309f91434c658ebd27
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744591"
---
# <a name="idiaenumframedatanext"></a>IDiaEnumFrameData::Next
抓取列舉序列中指定數目的框架資料元素。

## <a name="syntax"></a>語法

```C++
HRESULT Next ( 
   ULONG           celt,
   IDiaFrameData** rgelt,
   ULONG*          pceltFetched
);
```

#### <a name="parameters"></a>參數
 celt

在列舉值中要抓取的框架資料元素數目。

 rgelt

脫銷要在要求的框架資料元素中填入的[IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)物件陣列。

 pceltFetched

脫銷傳回已提取枚舉器中的框架資料元素數目。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 如果沒有其他記錄，則傳回 `S_FALSE`。 否則會傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)