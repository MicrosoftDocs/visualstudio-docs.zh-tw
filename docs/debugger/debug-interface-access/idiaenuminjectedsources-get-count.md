---
description: 抓取插入的來源數目。
title: IDiaEnumInjectedSources::get_Count | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::get_Count method
ms.assetid: 659c415b-9f7b-470d-90e2-b4c0087f8dd3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f140dbeb347db9e7085365cc7c3ba8cddcaff927
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149015"
---
# <a name="idiaenuminjectedsourcesget_count"></a>IDiaEnumInjectedSources::get_Count
抓取插入的來源數目。

## <a name="syntax"></a>語法

```C++
HRESULT get_Count ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>參數
 pRetVal

擴展傳回插入的來源數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)
