---
title: marker_series::write_alert 方法 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic:marker_series::write_alert
helpviewer_keywords:
- Concurrency::diagnostic:marker_series::write_alert method
ms.assetid: 9d5465c7-f862-47a7-b249-4116605075a6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b41cd976ddd637faf00ee50a3ec208d2b3d513f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54924937"
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
 **標頭：** *cvmarkersobj.h*  
  
 **命名空間：** Concurrency::diagnostic  
  
## <a name="see-also"></a>另請參閱  
 [marker_series 類別](../profiling/marker-series-class.md)