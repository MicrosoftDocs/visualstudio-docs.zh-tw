---
title: span 類別 | Microsoft Docs
description: 瞭解 span 類別，以及它如何定義應用程式的階段。 同時瞭解範圍類別公用的函式和繼承階層。
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::span
helpviewer_keywords:
- Concurrency::diagnostic::span class
ms.assetid: 527826a8-2590-43ad-b907-7bc0b7288e92
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fff7f91326cac47100f5b2b1b42e22b9c0fc1d9b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949957"
---
# <a name="span-class"></a>span 類別
定義應用程式階段。

## <a name="syntax"></a>語法

```cpp
class span;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[span::span 建構函式](../profiling/span-span-constructor.md)|初始化 `span` 類別的新執行個體。|
|[span::~span 解構函式](../profiling/span-tilde-span-destructor.md)|終結 `span` 物件，並釋放其資源。|

## <a name="inheritance-hierarchy"></a>繼承階層架構
 `span`

## <a name="requirements"></a>規格需求
 **標頭：** *cvmarkersobj.h*

 **命名空間：** Concurrency::diagnostic

## <a name="see-also"></a>另請參閱
- [診斷命名空間](../profiling/diagnostic-namespace.md)