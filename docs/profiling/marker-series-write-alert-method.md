---
title: marker_series::write_alert 方法 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic:marker_series::write_alert
helpviewer_keywords:
- Concurrency::diagnostic:marker_series::write_alert method
ms.assetid: 9d5465c7-f862-47a7-b249-4116605075a6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9ae17a44b37536359a5f09fd75fda82ce34b50c3
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/11/2018
---
# <a name="markerserieswritealert-method"></a>marker_series::write_alert 方法
將警示寫入並行視覺化檢視追蹤檔。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void write_alert(  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### <a name="parameters"></a>參數  
 `_Format`  
 複合格式字串，其中包含混合零或多個格式項目的文字，並與引數清單中的物件相對應。  
  
## <a name="requirements"></a>需求  
 **標頭：** cvmarkersobj.h  
  
 **命名空間：** Concurrency::diagnostic  
  
## <a name="see-also"></a>請參閱  
 [marker_series 類別](../profiling/marker-series-class.md)