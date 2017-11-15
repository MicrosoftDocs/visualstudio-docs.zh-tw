---
title: "marker_series::marker_series 建構函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cvmarkersobj/Concurrency::diagnostic::marker_series::marker_series
helpviewer_keywords: Concurrency::diagnostic::marker_series constructor
ms.assetid: 042c7d23-f1d8-4e09-9e76-a21c30243790
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 83922b913e810042bef82eb0b81a0e42f8d3bbb1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="markerseriesmarkerseries-constructor"></a>marker_series::marker_series 建構函式
初始化 `marker_series` 類別的新執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
marker_series();  
marker_series(  
   _In_ LPCTSTR _SeriesName  
);  
marker_series(  
   _In_ const GUID* _ProviderGuid  
);  
marker_series(  
   _In_ const GUID* _ProviderGuid,  
   _In_ LPCTSTR _SeriesName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `_SeriesName`  
 要建立的系列名稱。  
  
 `_ProviderGuid`  
 系列提供者的 GUID。  
  
## <a name="requirements"></a>需求  
 **標頭：**cvmarkersobj.h  
  
 **命名空間：**Concurrency::diagnostic  
  
## <a name="see-also"></a>另請參閱  
 [marker_series 類別](../profiling/marker-series-class.md)