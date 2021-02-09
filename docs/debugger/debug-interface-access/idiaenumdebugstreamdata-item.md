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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c9c094d389b26424ef8b9fbeec9aeaf8de054441
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857052"
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

在要抓取之記錄的索引。 索引位於0到-1 的範圍內 `count` ，其中 `count` 是 [IDiaEnumDebugStreamData：： get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)所傳回的。

 cbData

在資料緩衝區的大小（以位元組為單位）。

 pcbData

擴展傳回傳回的位元組數目。 如果 `data` 為 `NULL` ，則 `pcbData` 包含指定記錄中可用資料的位元組總數。

 data[]

擴展使用 debug stream 記錄資料填入的緩衝區。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。 `E_INVALIDARG`如果參數超出範圍，則傳回不正確參數 `index` 。

## <a name="see-also"></a>另請參閱
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
- [IDiaEnumDebugStreamData::Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)
- [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)
- [IDiaEnumDebugStreamData::get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)
- [IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)