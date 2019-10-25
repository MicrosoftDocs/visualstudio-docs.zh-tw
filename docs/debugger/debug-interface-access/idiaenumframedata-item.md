---
title: IDiaEnumFrameData::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 9c15f395e7f4aa576c5f69b0f1c61f37ca808fb6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744606"
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

在要抓取的[IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)物件索引。 索引的範圍是0到 `count`-1，其中 `count` 是由[IDiaEnumFrameData：： get_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md)方法傳回。

 section

脫銷傳回[IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)物件，代表所需的框架資料元素。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)