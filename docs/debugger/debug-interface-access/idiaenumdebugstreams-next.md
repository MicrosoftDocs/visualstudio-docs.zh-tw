---
description: 抓取列舉順序中指定數目的 debug 資料流程。
title: IDiaEnumDebugStreams：： Next |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Next method
ms.assetid: eb8eae5a-be27-45f4-a7bd-6e4ef0652385
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 645c04005263372df120f976e9dd402160594855
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158117"
---
# <a name="idiaenumdebugstreamsnext"></a>IDiaEnumDebugStreams::Next
抓取列舉順序中指定數目的 debug 資料流程。

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

在要抓取的列舉值中的 debug 資料流程數目。

 rgelt

擴展傳回 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) 物件的陣列，表示要抓取的偵錯工具資料流程。

 pceltFetched

擴展傳回傳回的偵錯工具資料流程數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果沒有資料流程，則傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)
