---
title: ResumeTracking | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- ResumeTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- ResumeTracking
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e2ff32a4eb2218a8b3d09188c787156e484147f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996694"
---
# <a name="resumetracking"></a>ResumeTracking
在目前的內容中繼續追蹤。

## <a name="syntax"></a>語法

```cpp
HRESULT WINAPI ResumeTracking();
```

## <a name="return-value"></a>傳回值
 如已繼續追蹤，則為 **HRESULT** 和已設定的 **SUCCEEDED** 位元。 如果因為無法取得內容而無法繼續追蹤，則傳回 **E_FAIL**。

## <a name="requirements"></a>需求
 **標頭：***FileTracker.h*

## <a name="see-also"></a>另請參閱
- [SuspendTracking](../msbuild/suspendtracking.md)