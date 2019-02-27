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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee3f02be5494f85c0fa36be510f0a0c25caf53b6
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56704315"
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
 **標頭：***FileTracker.h*

## <a name="see-also"></a>另請參閱
- [WriteContextTLogs](../msbuild/writecontexttlogs.md)