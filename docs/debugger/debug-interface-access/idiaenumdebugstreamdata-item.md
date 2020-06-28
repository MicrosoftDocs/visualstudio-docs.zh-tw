---
title: IDiaEnumDebugStreamData：： Item |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Item method
ms.assetid: 761e61a5-44a6-4d5d-a98e-c2e9b89d2343
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4696d8fdab9720796db1c6b5dff25b7bcfe49e01
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468452"
---
# <a name="idiaenumdebugstreamdataitem"></a>IDiaEnumDebugStreamData::Item
抓取指定的記錄。

## <a name="syntax"></a>語法

```C++
HRESULT Item ( 
   DWORD  index,
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>參數
 索引

在要抓取之記錄的索引。 索引的範圍是0到 `count` -1，其中 `count` 是由[IDiaEnumDebugStreamData：： get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)傳回。

 cbData

在資料緩衝區的大小（以位元組為單位）。

 pcbData

脫銷傳回傳回的位元組數目。 如果 `data` 為 `NULL` ，則 `pcbData` 包含指定記錄中可用的資料位元組總數。

 data[]

脫銷以 debug 資料流程記錄資料填入的緩衝區。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。 `E_INVALIDARG`如果參數超出範圍，則傳回無效參數的 `index` 。

## <a name="see-also"></a>另請參閱
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
- [IDiaEnumDebugStreamData::Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)
- [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)
- [IDiaEnumDebugStreamData::get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)
- [IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)