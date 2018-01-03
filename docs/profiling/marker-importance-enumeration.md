---
title: "marker_importance 列舉 |Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords: Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ae7bb9f300a1d57707966a3b4dbae202eea78d8c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="markerimportance-enumeration"></a>marker_importance 列舉
表示並行視覺化檢視標記的重要性層級。  
  
## <a name="syntax"></a>語法  
  
```  
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
 **標頭：**cvmarkersobj.h  
  
 **命名空間：**Concurrency::diagnostic  
  
## <a name="see-also"></a>請參閱  
 [diagnostic 命名空間](../profiling/diagnostic-namespace.md)