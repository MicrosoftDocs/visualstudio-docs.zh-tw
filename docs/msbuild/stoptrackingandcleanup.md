---
title: StopTrackingAndCleanup | Microsoft Docs
description: 瞭解 MSBuild 如何使用 StopTrackingAndCleanup 來停止追蹤會話所使用的所有追蹤和釋放記憶體。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StopTrackingAndCleanup
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05aec8bc85ac392670469da8073da02888b2f063
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048098"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup

停止所有的追蹤，並釋放追蹤工作階段使用的所有記憶體。

## <a name="syntax"></a>語法

```cpp
HRESULT WINAPI StopTrackingAndCleanup(void);
```

## <a name="return-value"></a>傳回值

 如已停止追蹤，則傳回 **HRESULT** 和已設定的 **SUCCEEDED** 位元。

## <a name="requirements"></a>規格需求

 **標頭：** *FileTracker.h*

## <a name="see-also"></a>請參閱

- [StartTrackingContext](../msbuild/starttrackingcontext.md)