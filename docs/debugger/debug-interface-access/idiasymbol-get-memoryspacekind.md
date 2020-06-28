---
title: IDiaSymbol：： get_memorySpaceKind |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9a63b298-8577-4c15-8595-530558d41bf1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 55edae0904a0f3416fc30a3776b81414e57a6525
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85462900"
---
# <a name="idiasymbolget_memoryspacekind"></a>IDiaSymbol::get_memorySpaceKind
抓取記憶體空間種類。

## <a name="syntax"></a>語法

```C++
HRESULT get_memorySpaceKind(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷`DWORD`包含記憶體空間種類之的指標。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)