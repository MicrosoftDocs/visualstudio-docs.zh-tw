---
title: IDiaLoadCallback2::RestrictDBGAccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictDBGAccess method
ms.assetid: 63b67a93-2910-4fff-aa70-6b2eaa08e5c8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8fd54587127d434f79cf8d80aa130f5135bb7aeb
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466711"
---
# <a name="idialoadcallback2restrictdbgaccess"></a>IDiaLoadCallback2::RestrictDBGAccess
決定是否允許從 dbg 檔案尋找 debug 資訊。

## <a name="syntax"></a>語法

```C++
HRESULT RestrictDBGAccess();
```

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="remarks"></a>備註
 以外的任何傳回值 `S_OK` ，以防止從 dbg 檔案尋找 debug 資訊。

## <a name="see-also"></a>另請參閱
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)