---
title: IDiaEnumDebugStreamData：： Next |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 117d16a9c010bbed2c14544f6cc94c4782701e34
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468445"
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

脫銷傳回傳回的位元組數目。 如果 `data` 是 Null，則會 `pcbData` 包含所有要求的記錄可用的資料位元組總數。

 data[]

脫銷要填入 debug 資料流程記錄資料的緩衝區。

 pceltFetched

[in、out]傳回中的記錄數目 `data` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 如果沒有其他記錄，則傳回 `S_FALSE` 。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
- [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)