---
title: IDiaLoadCallback2::RestrictSystemRootAccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictSystemRootAccess method
ms.assetid: 39f22db8-632a-4ef0-babc-23f758e6d937
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0cf1a29019de2d3ffdfdb3cc7b9006e964495aa9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742978"
---
# <a name="idialoadcallback2restrictsystemrootaccess"></a>IDiaLoadCallback2::RestrictSystemRootAccess
決定是否允許在系統根目錄中搜尋 .pdb 檔案。

## <a name="syntax"></a>語法

```C++
HRESULT RestrictSystemRootAccess();
```

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 除了 `S_OK` 以外的任何傳回碼，都不會在系統根目錄中搜尋 .pdb 檔案。

## <a name="see-also"></a>請參閱
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)