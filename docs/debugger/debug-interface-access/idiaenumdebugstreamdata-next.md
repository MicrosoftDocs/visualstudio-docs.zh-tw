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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9eb951dd2362b93c61e835da78e5e02d6dc67069
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857038"
---
# <a name="idiaenumdebugstreamdatanext"></a>IDiaEnumDebugStreamData::Next
捕獲列舉序列中指定的記錄數目。

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

在要取出的記錄數目。

 cbData

在資料緩衝區的大小（以位元組為單位）。

 pcbData

擴展傳回傳回的位元組數目。 如果 `data` 是 Null，則 `pcbData` 包含所有所要求記錄的可用資料位元組總數。

 data[]

擴展要填入 debug stream 記錄資料的緩衝區。

 pceltFetched

[in，out]傳回中的記錄數目 `data` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 如果沒有其他記錄，則傳回 `S_FALSE` 。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
- [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)