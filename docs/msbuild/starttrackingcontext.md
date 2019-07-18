---
title: StartTrackingContext | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c395df1e08f1b4e33e9cd34fec54bdd044f3b4c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62939205"
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

## <a name="requirements"></a>需求
 **標頭：** *FileTracker.h*