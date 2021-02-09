---
title: WriteContextTLogs | Microsoft Docs
description: 瞭解 WriteCoNtextTLogs 的語法、需求和傳回值，以寫入目前內容的記錄檔。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteContextTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteContextTLogs
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b44777f41c4fac3d36cb79222d48a93c5c1cf0b7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888000"
---
# <a name="writecontexttlogs"></a>WriteContextTLogs

寫入目前內容的記錄檔。

## <a name="syntax"></a>語法

```cpp
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
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

- [WriteAllTLogs](../msbuild/writealltlogs.md)