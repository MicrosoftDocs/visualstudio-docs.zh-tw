---
title: SuspendTracking | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- SuspendTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SuspendTracking
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cc2a8b3dc2f5940c64be870df452b088dce7bc0e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56632455"
---
# <a name="suspendtracking"></a>SuspendTracking
在目前的內容中暫停追蹤。

## <a name="syntax"></a>語法

```cpp
HRESULT WINAPI SuspendTracking(void);
```

## <a name="return-value"></a>傳回值
 如已暫停追蹤，則為 **HRESULT** 和已設定的 **SUCCEEDED** 位元。

## <a name="requirements"></a>需求
 **標頭：***FileTracker.h*

## <a name="see-also"></a>另請參閱
- [ResumeTracking](../msbuild/resumetracking.md)