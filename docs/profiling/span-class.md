---
title: span 類別 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::span
helpviewer_keywords:
- Concurrency::diagnostic::span class
ms.assetid: 527826a8-2590-43ad-b907-7bc0b7288e92
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d8f31d24dc6c6c2ea20b50c9bf8af1cb4a9f9af
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56634704"
---
# <a name="span-class"></a>span 類別
定義應用程式階段。

## <a name="syntax"></a>語法

```cpp
class span;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[span::span 建構函式](../profiling/span-span-constructor.md)|初始化 `span` 類別的新執行個體。|
|[span::~span 解構函式](../profiling/span-tilde-span-destructor.md)|終結 `span` 物件，並釋放其資源。|

## <a name="inheritance-hierarchy"></a>繼承階層
 `span`

## <a name="requirements"></a>需求
 **標頭：** *cvmarkersobj.h*

 **命名空間：** Concurrency::diagnostic

## <a name="see-also"></a>另請參閱
- [diagnostic 命名空間](../profiling/diagnostic-namespace.md)