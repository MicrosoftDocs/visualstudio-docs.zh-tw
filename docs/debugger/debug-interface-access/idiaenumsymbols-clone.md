---
title: 'Idiaenumsymbols:: Clone |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 098dd1f5ba12c5b3aeff6add364f63b8baa676bc
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56620144"
---
# <a name="idiaenumsymbolsclone"></a>IDiaEnumSymbols::Clone
建立列舉值，包含目前的列舉值相同的列舉型別狀態。

## <a name="syntax"></a>語法

```C++
HRESULT Clone ( 
   IDiaEnumSymbols** ppenum
);
```

#### <a name="parameters"></a>參數
 ppenum

[out]傳回[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)物件，包含列舉值重複。 符號不會重複，列舉值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)