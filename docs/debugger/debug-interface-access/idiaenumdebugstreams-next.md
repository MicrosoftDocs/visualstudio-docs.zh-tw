---
title: 'Idiaenumdebugstreams:: Next |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Next method
ms.assetid: eb8eae5a-be27-45f4-a7bd-6e4ef0652385
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a1b7819c90804933795c220c4d47f288d29abfe1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838294"
---
# <a name="idiaenumdebugstreamsnext"></a>IDiaEnumDebugStreams::Next
擷取指定的數目的列舉型別序列中的偵錯資料流。

## <a name="syntax"></a>語法

```C++
HRESULT Next ( 
   ULONG                     celt,
   IDiaEnumDebugStreamData** rgelt,
   ULONG*                    pceltFetched
);
```

#### <a name="parameters"></a>參數
 celt

[in]要擷取列舉值中的偵錯資料流數目。

 rgelt

[out]傳回的陣列[IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)物件，表示偵錯資料流擷取。

 pceltFetched

[out]傳回傳回的偵錯資料流的數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 傳回`S_FALSE`如果沒有更多資料流。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)