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
ms.openlocfilehash: 36b48529f82a908ea765151561a71c58cd2c7bc5
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578427"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot
使用指定根標記的回應檔啟動追蹤內容。

## <a name="syntax"></a>語法

```cpp
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);
```

#### <a name="parameters"></a>參數
[輸入] `intermediateDirectory`

 儲存追蹤記錄的目錄。

[輸入] `taskName`

 找到追蹤內容。 這個名稱是用來建立記錄檔的名稱。

[輸入] `rootMarkerResponseFile`

 包含根標記的回應檔路徑名稱。 根名稱是用來將內容所有的追蹤集合在一起。

## <a name="return-value"></a>傳回值
 如已建立追蹤內容，則為 **HRESULT** 和已設定的 **SUCCEEDED** 位元。

## <a name="requirements"></a>需求
 **標頭：** *FileTracker .h*

## <a name="see-also"></a>另請參閱
- [StartTrackingContext](../msbuild/starttrackingcontext.md)