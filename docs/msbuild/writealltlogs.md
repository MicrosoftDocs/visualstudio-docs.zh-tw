---
title: WriteAllTLogs | Microsoft Docs
description: 瞭解 WriteAllTLogs 的語法、需求和傳回值，其會為所有線程和內容寫入追蹤記錄。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteAllTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteAllTLogs
ms.assetid: 1fa3e10b-263c-4960-a9ad-485c02a7a872
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 65e0610c8148ab6ff32d8c19f6fd378ba46d76d5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933592"
---
# <a name="writealltlogs"></a>WriteAllTLogs

寫入所有執行緒和內容的追蹤記錄檔。

## <a name="syntax"></a>語法

```cpp
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
```

#### <a name="parameters"></a>參數

[in] `intermediateDirectory`

 儲存追蹤記錄的目錄。

[in] `tlogRootName`

 記錄檔名稱的根名稱。

## <a name="return-value"></a>傳回值

 如已建立追蹤內容，則為 **HRESULT** 和已設定的 **SUCCEEDED** 位元。

## <a name="requirements"></a>規格需求

 **標頭：** *FileTracker.h*

## <a name="see-also"></a>另請參閱

- [WriteContextTLogs](../msbuild/writecontexttlogs.md)