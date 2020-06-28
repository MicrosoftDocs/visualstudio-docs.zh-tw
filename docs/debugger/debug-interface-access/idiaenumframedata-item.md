---
title: IDiaEnumFrameData::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Item method
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0de3a87d62195ae28e83efefa641dde5667f0a6d
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468326"
---
# <a name="idiaenumframedataitem"></a>IDiaEnumFrameData::Item
藉由索引來抓取框架資料元素。

## <a name="syntax"></a>語法

```C++
HRESULT Item ( 
   DWORD           index,
   IDiaFrameData** section
);
```

#### <a name="parameters"></a>參數
 索引

在要抓取的[IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)物件索引。 索引的範圍是0到 `count` -1，其中 `count` 是由[IDiaEnumFrameData：： get_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md)方法所傳回。

 section

脫銷傳回[IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)物件，代表所需的框架資料元素。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)