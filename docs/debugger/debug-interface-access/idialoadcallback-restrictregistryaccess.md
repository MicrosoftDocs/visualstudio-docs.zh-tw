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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18436d28fbee7ba12cea2398eb1fa6abbd8ac23b
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466732"
---
# <a name="idialoadcallbackrestrictregistryaccess"></a>IDiaLoadCallback::RestrictRegistryAccess
判斷是否可以使用登錄查詢來尋找符號搜尋路徑。

## <a name="syntax"></a>語法

```C++
HRESULT RestrictRegistryAccess();
```

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="remarks"></a>備註
 以外的任何傳回碼 `S_OK` 會防止查詢登錄中的符號搜尋路徑。

## <a name="see-also"></a>另請參閱
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)