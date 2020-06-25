---
title: marker_series::marker_series 建構函式 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_series::marker_series
helpviewer_keywords:
- Concurrency, diagnostic::marker_series constructor
ms.assetid: 042c7d23-f1d8-4e09-9e76-a21c30243790
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78b2e80611983e69f11465269dcf15dad7d6351e
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85329704"
---
# <a name="marker_seriesmarker_series-constructor"></a>marker_series::marker_series 建構函式
將 `marker_series` 類別的新執行個體初始化。

## <a name="syntax"></a>語法

```cpp
marker_series();
marker_series(
   _In_ LPCTSTR _SeriesName
);
marker_series(
   _In_ const GUID* _ProviderGuid
);
marker_series(
   _In_ const GUID* _ProviderGuid,
   _In_ LPCTSTR _SeriesName
);
```

#### <a name="parameters"></a>參數
 `_SeriesName` 要建立的系列名稱。

 `_ProviderGuid` 系列提供者的 GUID。

## <a name="requirements"></a>規格需求
 **標頭：** *cvmarkersobj.h*

 **命名空間：** Concurrency::diagnostic

## <a name="see-also"></a>另請參閱
- [marker_series 類別](../profiling/marker-series-class.md)