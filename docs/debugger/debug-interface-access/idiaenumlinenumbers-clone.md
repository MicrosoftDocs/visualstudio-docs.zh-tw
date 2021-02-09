---
title: IDiaEnumLineNumbers：： Clone |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Clone method
ms.assetid: fcd2479a-8ff7-4aba-a737-06123c280d54
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c8593fca731f96bb0d04b7cba12143eaf65614bf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856618"
---
# <a name="idiaenumlinenumbersclone"></a>IDiaEnumLineNumbers::Clone
建立包含與目前列舉值相同列舉狀態的列舉值。

## <a name="syntax"></a>語法

```C++
HRESULT Clone ( 
   IDiaEnumLineNumbers** ppenum
);
```

#### <a name="parameters"></a>參數
 `ppenum`

擴展傳回包含重複列舉值的 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) 物件。 行號不會重複，只會複製列舉值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)