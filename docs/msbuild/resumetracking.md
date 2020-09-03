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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 248bb5e5e01b8209f826478e90b2c60b70922987
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "77632494"
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

 **標頭：** *FileTracker.h*

## <a name="see-also"></a>另請參閱

- [SuspendTracking](../msbuild/suspendtracking.md)