---
title: marker_series 類別 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cb199d74ade593d0bc8318c27bc96ffbf70e4dcf
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54778866"
---
# <a name="markerseries-class"></a>marker_series 類別
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

表示由單一提供者產生之事件的序列通道。  
  
## <a name="syntax"></a>語法  
  
```  
class marker_series;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[marker_series::marker_series 建構函式](../profiling/marker-series-marker-series-constructor.md)|初始化 `marker_series` 類別的新執行個體。|  
|[marker_series::~marker_series 解構函式](../profiling/marker-series-tilde-marker-series-destructor.md)|終結 marker_series 物件並釋放所有配置的資源。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[marker_series::is_enabled 方法](../profiling/marker-series-is-enabled-method.md)|判斷是否有任何工作階段啟用該提供者。|  
|[marker_series::write_alert 方法](../profiling/marker-series-write-alert-method.md)|將警示寫入並行視覺化檢視追蹤檔。|  
|[marker_series::write_flag 方法](../profiling/marker-series-write-flag-method.md)|將旗標寫入並行視覺化檢視追蹤檔。|  
|[marker_series::write_message 方法](../profiling/marker-series-write-message-method.md)|將訊息寫入並行視覺化檢視追蹤檔。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `marker_series`  
  
## <a name="requirements"></a>需求  
 **標頭：** cvmarkersobj.h  
  
 **命名空間：** Concurrency::diagnostic  
  
## <a name="see-also"></a>請參閱  
 [diagnostic 命名空間](../profiling/diagnostic-namespace.md)
