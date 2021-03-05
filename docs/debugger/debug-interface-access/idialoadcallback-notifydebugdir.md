---
description: 當在 .exe 檔中找到 debug 目錄時呼叫。
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ed83b79dea8f488be79a2161968876c9aa2a9a11
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148280"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
當在 .exe 檔中找到 debug 目錄時呼叫。

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

[in] `TRUE` 如果從可執行檔讀取 debug 目錄（而不是) dbg 檔案） (。

 `cbData`

在Debug 目錄中的資料位元組計數。

 `data[]`

在使用 debug 目錄填入的陣列。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。 通常會忽略傳回碼。

## <a name="remarks"></a>備註
 [IDiaDataSource：： loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法會在處理可執行檔時，在找到 debug 目錄時叫用此回呼。

 此方法可讓用戶端不需要對可執行檔和/或 debug 檔案進行反向工程，以支援在 .pdb 檔案中找到的 debug 資訊。 使用這項資料，用戶端可以辨識可用的偵錯工具資訊類型，以及它是否位於可執行檔或 dbg 檔案中。

 大部分的用戶端都不需要此回呼 `IDiaDataSource::loadDataForExe` ，因為在提供符號的必要時，方法會以透明方式開啟 .pdb 和 dbg 檔。

## <a name="see-also"></a>另請參閱
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
