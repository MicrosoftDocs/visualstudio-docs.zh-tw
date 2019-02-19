---
title: marker_importance 列舉 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a4451a7b222b66f0fe5bea2b0e5f2b8499c9033c
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54779033"
---
# <a name="markerimportance-enumeration"></a>marker_importance 列舉
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 **標頭：** cvmarkersobj.h  
  
 **命名空間：** Concurrency::diagnostic  
  
## <a name="see-also"></a>請參閱  
 [diagnostic 命名空間](../profiling/diagnostic-namespace.md)
