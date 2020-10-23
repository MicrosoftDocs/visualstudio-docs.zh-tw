---
title: EndTrackingContext | Microsoft Docs
description: 瞭解使用 MSBuild EndTrackingCoNtext 結束目前追蹤內容的語法、傳回值和需求。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: da1ef921106732a7787f68a979bc88f3ac012b6d
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436666"
---
# <a name="endtrackingcontext"></a>EndTrackingContext

結束目前追蹤內容。

## <a name="syntax"></a>語法

```cpp
HRESULT WINAPI EndTrackingContext();
```

## <a name="return-value"></a>傳回值

如果已結束追蹤內容，則為已設定 **SUCCEEDED** 位元的 **HRESULT**。

## <a name="requirements"></a>規格需求

**標頭：** *FileTracker.h*

## <a name="see-also"></a>另請參閱

- [StartTrackingContext](../msbuild/starttrackingcontext.md)
