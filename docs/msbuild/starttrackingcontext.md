---
title: StartTrackingContext | Microsoft Docs
description: 瞭解 MSBuild StartTrackingCoNtext 的參數、需求和傳回值，此值會啟動追蹤內容。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StartTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StartTrackingContext
ms.assetid: 720cd295-38e7-4974-86db-b8106b1207ba
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 15121f050fd5af9a5cb36ce15ffc2161076df06d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929117"
---
# <a name="starttrackingcontext"></a>StartTrackingContext

啟動追蹤內容。

## <a name="syntax"></a>語法

```cpp
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);
```

#### <a name="parameters"></a>參數

[in] `intermediateDirectory`

 儲存追蹤記錄的目錄。

[in] `taskName`

 找到追蹤內容。 這個名稱是用來建立記錄檔的名稱。

## <a name="return-value"></a>傳回值

 如已建立追蹤內容，則為 **HRESULT** 和已設定的 **SUCCEEDED** 位元。

## <a name="requirements"></a>規格需求

 **標頭：** *FileTracker.h*
