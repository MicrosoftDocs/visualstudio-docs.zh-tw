---
title: 'Idiaenumdebugstreamdata:: Next |Microsoft Docs'
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
ms.openlocfilehash: cf641fde4c03053496c732aa7904ddcad671af20
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56695631"
---
# <a name="idiaenumdebugstreamdatanext"></a>IDiaEnumDebugStreamData::Next
擷取指定的列舉順序中的記錄數。

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

[in]要擷取的記錄數目。

 cbData

[in]資料緩衝區，以位元組為單位的大小。

 pcbData

[out]傳回動作傳回的位元組的數目。 如果`data`是 NULL，則`pcbData`所有要求的記錄包含的可用資料的位元組總數。

 data[]

[out]要填滿偵錯資料流記錄資料的緩衝區。

 pceltFetched

[in、 out]傳回的記錄數目`data`。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 傳回`S_FALSE`如果沒有更多的記錄。 否則會傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
- [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)