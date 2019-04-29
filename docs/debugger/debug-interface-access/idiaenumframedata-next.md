---
title: 'Idiaenumframedata:: Next |Microsoft Docs'
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
ms.openlocfilehash: 55875d4ad964b958bf2fb38d259e7d4d68909cb5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830101"
---
# <a name="idiaenumframedatanext"></a>IDiaEnumFrameData::Next
擷取框架資料元素，列舉序列中指定的數目。

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

[in]要擷取列舉值中的框架資料元素數目。

 rgelt

[out]陣列[IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)填入要求的框架資料元素的物件。

 pceltFetched

[out]擷取列舉值中傳回畫面格的資料元素的數目。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 傳回`S_FALSE`如果沒有更多的記錄。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)