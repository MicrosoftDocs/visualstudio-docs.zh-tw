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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 950c6a07a46f7f4b970912e576257a577021367e
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632003"
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

 **標頭：** *FileTracker .h*

## <a name="see-also"></a>另請參閱

- [ResumeTracking](../msbuild/resumetracking.md)