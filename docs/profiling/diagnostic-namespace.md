---
title: diagnostic 命名空間 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: d781bbfefa59b2e124cf76c11b8fd7c06cc66dda
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764666"
---
# <a name="diagnostic-namespace"></a>diagnostic 命名空間
`diagnostics` 命名空間提供的功能可用來發出並行視覺化檢視標記。  
  
## <a name="syntax"></a>語法  
  
```cpp  
namespace diagnostic;  
```  
  
## <a name="members"></a>成員  
  
### <a name="classes"></a>類別  
  
|名稱|描述|  
|----------|-----------------|  
|[marker_series 類別](../profiling/marker-series-class.md)|表示由單一提供者產生之事件的序列通道。|  
|[span 類別](../profiling/span-class.md)|定義應用程式階段。|  
  
### <a name="enumerations"></a>列舉  
  
|名稱|描述|  
|----------|-----------------|  
|[marker_importance 列舉](../profiling/marker-importance-enumeration.md)|表示並行視覺化檢視標記的重要性層級。|  
  
## <a name="requirements"></a>需求  
 **標頭：***cvmarkersobj.h*  
  
 **命名空間：** 並行  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (並行視覺化檢視)](../profiling/concurrency-namespace-concurrency-visualizer.md)