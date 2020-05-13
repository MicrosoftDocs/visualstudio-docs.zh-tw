---
title: WriteAllTLogs | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7eadb30ee25b1182be5deb12feebd5ef280ebf4b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630674"
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

## <a name="requirements"></a>需求

 **標頭：** *FileTracker.h*

## <a name="see-also"></a>另請參閱

- [WriteContextTLogs](../msbuild/writecontexttlogs.md)