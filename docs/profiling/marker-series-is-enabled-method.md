---
title: marker_series::is_enabled 方法 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::is_enabled
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::is_enabled method
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 22a7baa08a29cd77506e48762179118b3bbb2d1a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "63002760"
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
- [marker_series類](../profiling/marker-series-class.md)