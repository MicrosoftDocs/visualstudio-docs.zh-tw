---
title: IDiaEnumSymbols：： Clone |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Clone method
ms.assetid: 5c542025-98cf-4307-901f-b9430f780cf0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4621c25daf8b8c8415f84eb87f06e7223ff30cf3
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467796"
---
# <a name="idiaenumsymbolsclone"></a>IDiaEnumSymbols::Clone
建立枚舉器，其中包含與目前列舉值相同的列舉狀態。

## <a name="syntax"></a>語法

```C++
HRESULT Clone ( 
   IDiaEnumSymbols** ppenum
);
```

#### <a name="parameters"></a>參數
 ppenum

脫銷傳回[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)物件，其中包含重複的列舉值。 符號不會重複，只有枚舉器。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)