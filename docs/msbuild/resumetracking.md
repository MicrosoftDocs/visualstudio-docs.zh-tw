---
title: ResumeTracking | Microsoft Docs
description: 瞭解 MSBuild ResumeTracking 的語法、需求和傳回值，這會在目前的內容中繼續追蹤。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fd6722ca0b930d66a386732dac466a8e4fe36976
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937910"
---
# <a name="resumetracking"></a>ResumeTracking

在目前的內容中繼續追蹤。

## <a name="syntax"></a>語法

```cpp
HRESULT WINAPI ResumeTracking();
```

## <a name="return-value"></a>傳回值

 如已繼續追蹤，則為 **HRESULT** 和已設定的 **SUCCEEDED** 位元。 如果因為無法取得內容而無法繼續追蹤，則傳回 **E_FAIL**。

## <a name="requirements"></a>規格需求

 **標頭：** *FileTracker.h*

## <a name="see-also"></a>另請參閱

- [SuspendTracking](../msbuild/suspendtracking.md)