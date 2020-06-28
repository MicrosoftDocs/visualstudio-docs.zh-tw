---
title: IDiaLoadCallback::NotifyDebugDir | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 032e628512b7c601a6409f6f70ba0b0c3cabb37c
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466753"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
在 .exe 檔案中找到 debug 目錄時呼叫。

## <a name="syntax"></a>語法

```C++
HRESULT NotifyDebugDir ( 
   BOOL  fExecutable,
   DWORD cbData,
   BYTE  data[]
);
```

#### <a name="parameters"></a>參數
 `fExecutable`

[in] `TRUE`如果是從可執行檔（而不是 dbg 檔案）讀取 debug 目錄。

 `cbData`

在Debug 目錄中的資料位元組計數。

 `data[]`

在以 debug 目錄填入的陣列。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。 傳回碼通常會被忽略。

## <a name="remarks"></a>備註
 當[IDiaDataSource：： loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法在處理可執行檔時找到 debug 目錄時，會叫用此回呼。

 這個方法不需要讓用戶端對可執行檔和/或 debug 檔案進行反向工程，以支援在 .pdb 檔案中找到的 debug 以外的偵錯工具資訊。 透過這項資料，用戶端可以辨識可用的偵錯工具資訊類型，以及它是否位於可執行檔或 dbg 檔案中。

 大部分的用戶端都不需要此回呼 `IDiaDataSource::loadDataForExe` ，因為此方法會在需要提供符號時，以透明方式開啟 .pdb 和 dbg 檔案。

## <a name="see-also"></a>另請參閱
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)