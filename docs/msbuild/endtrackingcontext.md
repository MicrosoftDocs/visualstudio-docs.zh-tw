---
title: EndTrackingContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- EndTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- EndTrackingContext
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7f837e7a983d0f2c2520d7e379ffb49f332c75c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62821113"
---
# <a name="endtrackingcontext"></a>EndTrackingContext
結束目前追蹤內容。

## <a name="syntax"></a>語法

```cpp
HRESULT WINAPI EndTrackingContext();
```

## <a name="return-value"></a>傳回值
如果已結束追蹤內容，則為已設定 **SUCCEEDED** 位元的 **HRESULT**。

## <a name="requirements"></a>需求
**標頭：***FileTracker.h*

## <a name="see-also"></a>另請參閱
- [StartTrackingContext](../msbuild/starttrackingcontext.md)
