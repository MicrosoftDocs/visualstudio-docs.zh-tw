---
description: 表示並行視覺化檢視標記的重要性層級。
title: marker_importance 列舉 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_importance
helpviewer_keywords:
- Concurrency, diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2c2e7560c91882afe1ee2608bb2ae2fc105738dc
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223936"
---
# <a name="marker_importance-enumeration"></a>marker_importance 列舉
表示並行視覺化檢視標記的重要性層級。

## <a name="syntax"></a>語法

```cpp
enum marker_importance;
```

## <a name="members"></a>成員

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`critical_importance`|指定標記有極高重要性。|
|`high_importance`|指定標記有高重要性。|
|`low_importance`|指定標記有低重要性。|
|`normal_importance`|指定標記有一般重要性。|

## <a name="requirements"></a>規格需求
 **標頭：** *cvmarkersobj.h*

 **命名空間：** Concurrency::diagnostic

## <a name="see-also"></a>另請參閱
- [診斷命名空間](../profiling/diagnostic-namespace.md)
