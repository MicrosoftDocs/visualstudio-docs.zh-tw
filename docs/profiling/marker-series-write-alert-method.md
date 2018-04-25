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
ms.openlocfilehash: 8072fbee78312a5b44bff076e563c638a35d1d64
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="markerserieswritealert-method"></a>marker_series::write_alert 方法
將警示寫入並行視覺化檢視追蹤檔。  
  
## <a name="syntax"></a>語法  
  
```  
void write_alert(  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### <a name="parameters"></a>參數  
 `_Format`  
 複合格式字串，其中包含混合零或多個格式項目的文字，並與引數清單中的物件相對應。  
  
## <a name="requirements"></a>需求  
 **標頭：**cvmarkersobj.h  
  
 **命名空間：**Concurrency::diagnostic  
  
## <a name="see-also"></a>請參閱  
 [marker_series 類別](../profiling/marker-series-class.md)