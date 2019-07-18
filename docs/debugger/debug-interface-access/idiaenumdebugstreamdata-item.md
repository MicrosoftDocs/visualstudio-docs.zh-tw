---
title: 'Idiaenumdebugstreamdata:: Item |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 4f4a3e3f668789f98600cd649716413a57b13130
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838502"
---
# <a name="idiaenumdebugstreamdataitem"></a>IDiaEnumDebugStreamData::Item
擷取指定的記錄。

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

[in]要擷取記錄的索引。 索引是在範圍介於 0 到`count`-1，其中`count`會傳回[idiaenumdebugstreamdata:: Get_count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)。

 cbData

[in]資料緩衝區，以位元組為單位的大小。

 pcbData

[out]傳回動作傳回的位元組的數目。 如果`data`已`NULL`，然後`pcbData`包含可在指定的記錄資料的位元組總數。

 data[]

[out]偵錯資料流記錄資料會填入緩衝區。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。 傳回`E_INVALIDARG`無效的參數如果`index`參數超出範圍。

## <a name="see-also"></a>另請參閱
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
- [IDiaEnumDebugStreamData::Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)
- [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)
- [IDiaEnumDebugStreamData::get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)
- [IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)