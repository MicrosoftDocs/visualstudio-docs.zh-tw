---
title: "marker_series::write_message 方法 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cvmarkersobj/Concurrency::diagnostic::marker_series::write_message
helpviewer_keywords: Concurrency::diagnostic::marker_series::write_message method
ms.assetid: 546121bc-67e0-4a5a-a456-12bd78fd6de2
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8488bc30503ade516a9f03844bf56837540139d3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="markerserieswritemessage-method"></a>marker_series::write_message 方法
將訊息寫入並行視覺化檢視追蹤檔。  
  
## <a name="syntax"></a>語法  
  
```  
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
 `_Format`  
 複合格式字串，其中包含混合零或多個格式項目的文字，並與引數清單中的物件相對應。  
  
 `_Importance`  
 重要性層級。  
  
 `_Category`  
 分類。重要性層級。  
  
## <a name="requirements"></a>需求  
 **標頭：**cvmarkersobj.h  
  
 **命名空間：**Concurrency::diagnostic  
  
## <a name="see-also"></a>請參閱  
 [marker_series 類別](../profiling/marker-series-class.md)