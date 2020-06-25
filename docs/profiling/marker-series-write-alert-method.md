---
title: marker_series::write_alert 方法 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic:marker_series::write_alert
helpviewer_keywords:
- Concurrency, diagnostic:marker_series::write_alert method
ms.assetid: 9d5465c7-f862-47a7-b249-4116605075a6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5e79bab25885c8759ea5726b037771a4943c563
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85329636"
---
# <a name="marker_serieswrite_alert-method"></a>marker_series::write_alert 方法
將警示寫入並行視覺化檢視追蹤檔。

## <a name="syntax"></a>語法

```cpp
void write_alert(
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>參數
 `_Format` 複合格式字串，其中包含混合零或多個格式項目的文字，並與引數清單中的物件相對應。

## <a name="requirements"></a>規格需求
 **標頭：** *cvmarkersobj.h*

 **命名空間：** Concurrency::diagnostic

## <a name="see-also"></a>另請參閱
- [marker_series 類別](../profiling/marker-series-class.md)