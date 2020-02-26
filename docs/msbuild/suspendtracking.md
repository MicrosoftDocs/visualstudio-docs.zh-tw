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
ms.openlocfilehash: d48c29b9dcca477c5a5470c443be08d5060b413d
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578108"
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