---
description: 建立包含與目前資料表列舉值相同列舉狀態的列舉值。
title: IDiaEnumTables::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Clone method
ms.assetid: beb21109-b12c-44d8-8c1f-a332216b3713
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 410e02ab0a7a914c06b09b97a10fe3e2f3e3c630
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157893"
---
# <a name="idiaenumtablesclone"></a>IDiaEnumTables::Clone
建立包含與目前列舉值相同列舉狀態的列舉值。

## <a name="syntax"></a>語法

```C++
HRESULT Clone ( 
   IDiaEnumTables** ppenum
);
```

#### <a name="parameters"></a>參數
 `ppenum`

擴展傳回包含重複列舉值的 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md) 物件。 資料表不會重複，只會複製列舉值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
