---
title: IDiaEnumInjectedSources::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Item method
ms.assetid: 14846955-7270-451d-91d2-9cb34bb65187
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91be2f4f437cfeed30b0741d10bf719ba0ed2b71
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744508"
---
# <a name="idiaenuminjectedsourcesitem"></a>IDiaEnumInjectedSources::Item
藉由索引來抓取插入的來源。

## <a name="syntax"></a>語法

```C++
HRESULT Item ( 
   DWORD                index,
   IDiaInjectedSource** injectedSource
);
```

#### <a name="parameters"></a>參數
 索引

在要抓取的[IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)物件索引。 索引的範圍是0到 `count`-1，其中 `count` 是由[IDiaEnumInjectedSources：： get_Count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md)方法傳回。

 injectedSource

脫銷傳回代表插入之來源的[IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)物件。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)