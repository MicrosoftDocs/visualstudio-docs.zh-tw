---
description: 將訊息寫入並行視覺化檢視追蹤檔。
title: marker_series::write_message 方法 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_series::write_message
helpviewer_keywords:
- Concurrency, diagnostic::marker_series::write_message method
ms.assetid: 546121bc-67e0-4a5a-a456-12bd78fd6de2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 71a7e1783e470ee5ca1b7f1f18cd3d06cf1b5f49
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223871"
---
# <a name="marker_serieswrite_message-method"></a>marker_series::write_message 方法
將訊息寫入並行視覺化檢視追蹤檔。

## <a name="syntax"></a>語法

```cpp
void write_message(
   _In_ LPCTSTR _Format,
   ...
);
void write_message(
   marker_importance _Importance,
   _In_ LPCTSTR _Format,
   ...
);
void write_message(
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
void write_message(
   marker_importance _Importance,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>參數
 `_Format` 複合格式字串，其中包含混合零或多個格式項目的文字，並與引數清單中的物件相對應。

 `_Importance` 重要性層級。

 `_Category` 分類重要性層級。

## <a name="requirements"></a>規格需求
 **標頭：** *cvmarkersobj.h*

 **命名空間：** Concurrency::diagnostic

## <a name="see-also"></a>另請參閱
- [marker_series 類別](../profiling/marker-series-class.md)
