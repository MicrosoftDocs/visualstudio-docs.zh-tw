---
title: IDiaLoadCallback::RestrictRegistryAccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::RestrictRegistryAccess method
ms.assetid: de4760c3-a746-4bab-8065-1388fed31b67
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7cd793819bb0d8fdfb9e6c3b7c921c1dbf78ad22
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864675"
---
# <a name="idialoadcallbackrestrictregistryaccess"></a>IDiaLoadCallback::RestrictRegistryAccess
決定是否可以使用登錄查詢來尋找符號搜尋路徑。

## <a name="syntax"></a>語法

```C++
HRESULT RestrictRegistryAccess();
```

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 除了 `S_OK` 防止查詢登錄以進行符號搜尋路徑以外的任何傳回碼。

## <a name="see-also"></a>另請參閱
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)