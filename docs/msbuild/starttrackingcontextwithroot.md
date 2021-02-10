---
title: StartTrackingContextWithRoot | Microsoft Docs
description: 瞭解如何使用 MSBuild StartTrackingCoNtextWithRoot，以指定根標記的回應檔來啟動追蹤內容。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StartTrackingContextWithRoot
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StartTrackingContextWithRoot
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b52541c99fa81f31eddde8e6c12ad2eee04f3c20
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967042"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot

使用指定根標記的回應檔啟動追蹤內容。

## <a name="syntax"></a>語法

```cpp
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);
```

#### <a name="parameters"></a>參數

[in] `intermediateDirectory`

 儲存追蹤記錄的目錄。

[in] `taskName`

 找到追蹤內容。 這個名稱是用來建立記錄檔的名稱。

[in] `rootMarkerResponseFile`

 包含根標記的回應檔路徑名稱。 根名稱是用來將內容所有的追蹤集合在一起。

## <a name="return-value"></a>傳回值

 如已建立追蹤內容，則為 **HRESULT** 和已設定的 **SUCCEEDED** 位元。

## <a name="requirements"></a>規格需求

 **標頭：** *FileTracker.h*

## <a name="see-also"></a>另請參閱

- [StartTrackingContext](../msbuild/starttrackingcontext.md)