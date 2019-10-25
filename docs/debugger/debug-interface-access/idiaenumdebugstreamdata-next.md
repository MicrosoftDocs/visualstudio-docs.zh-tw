---
title: IDiaEnumDebugStreamData：： Next |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Next method
ms.assetid: 114171dd-38fd-4bd7-a702-8ff887ffc99b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: acdab0a565613194c67aa85484316a235c91dbf6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744786"
---
# <a name="idiaenumdebugstreamdatanext"></a>IDiaEnumDebugStreamData::Next
抓取列舉序列中指定數目的記錄。

## <a name="syntax"></a>語法

```C++
HRESULT Next ( 
   ULONG  celt,
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[],
   ULONG* pceltFetched
);
```

#### <a name="parameters"></a>參數
 celt

在要抓取的記錄數目。

 cbData

在資料緩衝區的大小（以位元組為單位）。

 pcbData

脫銷傳回傳回的位元組數目。 如果 `data` 是 Null，則 `pcbData` 包含所有要求的記錄可用的資料位元組總數。

 data[]

脫銷要填入 debug 資料流程記錄資料的緩衝區。

 pceltFetched

[in、out]傳回 `data` 中的記錄數目。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 如果沒有其他記錄，則傳回 `S_FALSE`。 否則會傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
- [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)