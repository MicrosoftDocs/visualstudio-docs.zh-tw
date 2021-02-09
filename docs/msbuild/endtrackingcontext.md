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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 90f4c8c4a83a496dba537e74dddfde4ae3f2f21a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877222"
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
