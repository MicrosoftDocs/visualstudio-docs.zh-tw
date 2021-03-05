---
description: 抓取列舉序列中指定的框架資料元素數目。
title: IDiaEnumFrameData：： Next |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Next method
ms.assetid: 546e2e23-efb2-425a-96a1-808c67c519fb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: adc27c29eedc98375f9feefc8872b5a75b7b219b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158033"
---
# <a name="idiaenumframedatanext"></a>IDiaEnumFrameData::Next
抓取列舉序列中指定的框架資料元素數目。

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

在要抓取的列舉值中的框架資料元素數目。

 rgelt

擴展要使用要求的框架資料元素填入的 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) 物件陣列。

 pceltFetched

擴展傳回已提取枚舉器中的框架資料項目數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 如果沒有其他記錄，則傳回 `S_FALSE` 。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
