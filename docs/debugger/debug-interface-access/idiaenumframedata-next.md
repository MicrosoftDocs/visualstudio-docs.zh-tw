---
title: IDiaEnumFrameData：： Next |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 2755ce3f48e22d239622dd49800e98ce49c496c7
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468319"
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
 如果成功，則傳回 `S_OK`。 如果沒有其他記錄，則傳回 `S_FALSE` 。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)