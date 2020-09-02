---
title: marker_series::is_enabled 方法 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_series::is_enabled
helpviewer_keywords:
- Concurrency, diagnostic::marker_series::is_enabled method
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ff6b0449c877b5ae925ba2088917d7bacab4c34
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85330675"
---
# <a name="marker_seriesis_enabled-method"></a>marker_series::is_enabled 方法
判斷是否有任何工作階段啟用該提供者。

## <a name="syntax"></a>語法

```cpp
bool is_enabled();
bool is_enabled(
   marker_importance _Importance,
   int _Category
);
```

#### <a name="parameters"></a>參數
 `_Importance` 重要性層級。

 `_Category` 分類。

## <a name="return-value"></a>傳回值

## <a name="requirements"></a>需求
 **標頭：** *cvmarkersobj.h*

 **命名空間：** Concurrency::diagnostic

## <a name="see-also"></a>另請參閱
- [marker_series 類別](../profiling/marker-series-class.md)