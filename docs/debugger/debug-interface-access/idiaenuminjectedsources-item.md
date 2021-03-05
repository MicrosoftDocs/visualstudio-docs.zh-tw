---
description: 藉由索引來抓取插入的來源。
title: IDiaEnumInjectedSources::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Item method
ms.assetid: 14846955-7270-451d-91d2-9cb34bb65187
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1d1ab3a9ce19705a4d9ff22f33a1275efc0e8b02
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148994"
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

在要抓取之 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) 物件的索引。 索引是從0到 `count` -1 的範圍，其中 `count` 是 [IDiaEnumInjectedSources：： get_Count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md) 方法所傳回的。

 injectedSource

擴展傳回代表插入來源的 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
