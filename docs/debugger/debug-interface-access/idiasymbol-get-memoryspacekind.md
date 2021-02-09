---
title: IDiaSymbol：： get_memorySpaceKind |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9a63b298-8577-4c15-8595-530558d41bf1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c763e681707d429591073ea9736a13ae5ad923d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862973"
---
# <a name="idiasymbolget_memoryspacekind"></a>IDiaSymbol::get_memorySpaceKind
捕獲記憶體空間種類。

## <a name="syntax"></a>語法

```C++
HRESULT get_memorySpaceKind(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展 `DWORD` 保存記憶體空間種類之的指標。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)