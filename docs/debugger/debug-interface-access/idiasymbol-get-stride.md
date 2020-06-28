---
title: IDiaSymbol::get_stride | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4264742a-3d91-44b9-9d14-87adbc77f0f0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f3853c6883ed5feab420f0b689c0c614d57aecd7
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461953"
---
# <a name="idiasymbolget_stride"></a>IDiaSymbol::get_stride
抓取矩陣或 strided 陣列的 stride。

## <a name="syntax"></a>語法

```C++
HRESULT get_stride(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷持有 stride 之的指標 `DWORD` 。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)