---
title: IDiaLoadCallback2::RestrictOriginalPathAccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 6bcdaa7c1896a0ef29706e3650ad8ac56537f778
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743004"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
判斷是否可以在原始 debug 目錄中尋找 .pdb 檔案。

## <a name="syntax"></a>語法

```C++
HRESULT RestrictOriginalPathAccess ();
```

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 除了 `S_OK` 以外的任何傳回碼，都不會在原始的 debug 目錄中尋找 .pdb 檔案。 原始的 debug 目錄是開啟偵錯工具時，編譯到可執行檔的符號檔的路徑。 這個路徑不一定與可執行檔所在的路徑相同。

## <a name="see-also"></a>請參閱
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)