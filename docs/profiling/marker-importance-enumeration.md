---
title: marker_importance 列舉 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 330ba15fa62272bd2c2f7ea7b40d6b527ab237c3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53841686"
---
# <a name="markerimportance-enumeration"></a>marker_importance 列舉
表示並行視覺化檢視標記的重要性層級。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum marker_importance;  
```  
  
## <a name="members"></a>成員  
  
### <a name="values"></a>值  
  
|名稱|說明|  
|----------|-----------------|  
|`critical_importance`|指定標記有極高重要性。|  
|`high_importance`|指定標記有高重要性。|  
|`low_importance`|指定標記有低重要性。|  
|`normal_importance`|指定標記有一般重要性。|  
  
## <a name="requirements"></a>需求  
 **標頭：** *cvmarkersobj.h*  
  
 **命名空間：** Concurrency::diagnostic  
  
## <a name="see-also"></a>另請參閱  
 [diagnostic 命名空間](../profiling/diagnostic-namespace.md)