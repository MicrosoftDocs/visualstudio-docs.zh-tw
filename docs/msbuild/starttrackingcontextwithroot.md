---
title: StartTrackingContextWithRoot | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68d585361b9797bf1df9c8b0b31f8a089e9de025
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632091"
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

## <a name="requirements"></a>需求

 **標頭：** *FileTracker.h*

## <a name="see-also"></a>另請參閱

- [StartTrackingContext](../msbuild/starttrackingcontext.md)