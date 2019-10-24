---
title: IDiaLoadCallback::NotifyDebugDir | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 6618440cab9b9042ec371383f6c809ca1d0d11f7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743094"
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

[in] `TRUE` 如果從可執行檔（而不是 dbg 檔案）讀取 debug 目錄，則為。

 `cbData`

在Debug 目錄中的資料位元組計數。

 `data[]`

在以 debug 目錄填入的陣列。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。 傳回碼通常會被忽略。

## <a name="remarks"></a>備註
 當[IDiaDataSource：： loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法在處理可執行檔時找到 debug 目錄時，會叫用此回呼。

 這個方法不需要讓用戶端對可執行檔和/或 debug 檔案進行反向工程，以支援在 .pdb 檔案中找到的 debug 以外的偵錯工具資訊。 透過這項資料，用戶端可以辨識可用的偵錯工具資訊類型，以及它是否位於可執行檔或 dbg 檔案中。

 大部分的用戶端都不需要此回呼，因為 `IDiaDataSource::loadDataForExe` 方法會在需要提供符號時，以透明的方式開啟 .pdb 和 dbg 檔案。

## <a name="see-also"></a>請參閱
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)