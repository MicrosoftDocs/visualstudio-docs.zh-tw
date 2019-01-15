---
title: diagnostic 命名空間 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic
helpviewer_keywords:
- Concurrency::diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c46f67281fe62de36472d9007f21841e843c20fa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53839439"
---
# <a name="diagnostic-namespace"></a>diagnostic 命名空間
`diagnostics` 命名空間提供的功能可用來發出並行視覺化檢視標記。  
  
## <a name="syntax"></a>語法  
  
```cpp  
namespace diagnostic;  
```  
  
## <a name="members"></a>成員  
  
### <a name="classes"></a>類別  
  
|名稱|說明|  
|----------|-----------------|  
|[marker_series 類別](../profiling/marker-series-class.md)|表示由單一提供者產生之事件的序列通道。|  
|[span 類別](../profiling/span-class.md)|定義應用程式階段。|  
  
### <a name="enumerations"></a>列舉  
  
|名稱|說明|  
|----------|-----------------|  
|[marker_importance 列舉](../profiling/marker-importance-enumeration.md)|表示並行視覺化檢視標記的重要性層級。|  
  
## <a name="requirements"></a>需求  
 **標頭：** *cvmarkersobj.h*  
  
 **命名空間：** 並行  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (並行視覺化檢視)](../profiling/concurrency-namespace-concurrency-visualizer.md)