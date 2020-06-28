---
title: IDiaEnumDebugStreams：： Next |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: e61e7c1d7d955c5586c19ec21a43fd4ab9abea5b
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468389"
---
# <a name="idiaenumdebugstreamsnext"></a>IDiaEnumDebugStreams::Next
在列舉序列中，捕獲指定數目的 debug 資料流程。

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

在列舉值中要抓取的 debug 資料流程數目。

 rgelt

脫銷傳回[IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)物件的陣列，代表要抓取的 debug 資料流程。

 pceltFetched

脫銷傳回傳回的 debug 資料流程數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 如果沒有其他資料流程，則傳回 `S_FALSE` 。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)