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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 62e8cf9ce14be5fd45c579584c754394f1dfb83b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945401"
---
# <a name="markerseriesisenabled-method"></a>marker_series::is_enabled 方法
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
 `_Importance`  
 重要性層級。  
  
 `_Category`  
 分類。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="requirements"></a>需求  
 **標頭：** *cvmarkersobj.h*  
  
 **命名空間：** Concurrency::diagnostic  
  
## <a name="see-also"></a>另請參閱  
 [marker_series 類別](../profiling/marker-series-class.md)