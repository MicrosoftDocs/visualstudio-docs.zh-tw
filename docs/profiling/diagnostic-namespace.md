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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 03671f314dca3c016f9524bcb246b74e0eb1f837
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "62970079"
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
 **標頭：** *cvmarkersobj.h*

 **命名空間：** 並行

## <a name="see-also"></a>另請參閱
- [併發命名空間（併發視覺化檢視）](../profiling/concurrency-namespace-concurrency-visualizer.md)