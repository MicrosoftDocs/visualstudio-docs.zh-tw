---
description: 藉由索引來抓取框架資料元素。
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c22983881c6f4e7d1bbb8e25ec6030d85411145c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149050"
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

在要抓取之 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) 物件的索引。 索引位於0到-1 的範圍內 `count` ，其中 `count` 是 [IDiaEnumFrameData：： get_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md) 方法所傳回的。

 section

擴展傳回 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) 物件，代表所需的框架資料元素。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
