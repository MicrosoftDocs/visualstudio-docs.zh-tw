---
title: IDiaLoadCallback2::RestrictOriginalPathAccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 784e17ddf6202419618b7ff3b8836f0f46021989
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85466683"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
決定是否可以在原始的 debug 目錄中尋找 .pdb 檔。

## <a name="syntax"></a>語法

```C++
HRESULT RestrictOriginalPathAccess ();
```

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 除了無法 `S_OK` 在原始的 debug 目錄中尋找 .pdb 檔之外，其他任何傳回碼都不會造成任何阻礙。 原始的 debug 目錄是開啟偵錯工具時，編譯成可執行檔的符號檔路徑。 這個路徑不一定與可執行檔所在的路徑相同。

## <a name="see-also"></a>另請參閱
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)