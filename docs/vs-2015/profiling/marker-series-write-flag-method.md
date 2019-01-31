---
title: marker_series::write_flag 方法 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersojb/Concurrency::diagnostic::marker_series::write_flag
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::write_flag method
ms.assetid: ca07f388-e5d5-46fd-b991-fe6e9029a68f
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b44c7cf2d2eb0f538b3819265298f1ca4166e6be
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834791"
---
# <a name="markerserieswriteflag-method"></a>marker_series::write_flag 方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

將旗標寫入並行視覺化檢視追蹤檔。  
  
## <a name="syntax"></a>語法  
  
```  
void write_flag(  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   marker_importance _Importance,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   marker_importance _Importance,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### <a name="parameters"></a>參數  
 `_Format`  
 複合格式字串，其中包含混合零或多個格式項目的文字，並與引數清單中的物件相對應。  
  
 `_Importance`  
 重要性層級。  
  
 `_Category`  
 分類。  
  
## <a name="requirements"></a>需求  
 **標頭：** cvmarkersobj.h  
  
 **命名空間：** Concurrency::diagnostic  
  
## <a name="see-also"></a>請參閱  
 [marker_series 類別](../profiling/marker-series-class.md)
