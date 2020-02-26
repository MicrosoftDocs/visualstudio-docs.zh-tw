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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b71f214a745222956c7dc9d582cc7fb2f1cfc427
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579696"
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
**標頭：** *FileTracker .h*

## <a name="see-also"></a>另請參閱
- [StartTrackingContext](../msbuild/starttrackingcontext.md)
