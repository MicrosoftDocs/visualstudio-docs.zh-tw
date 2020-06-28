---
title: IDiaSymbol：： get_numberOfColumns |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 64834351-e2c9-4f1c-9dc0-2abb5478bc63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69634b4f577607844b18e126018a0acd8d27ec9b
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85462745"
---
# <a name="idiasymbolget_numberofcolumns"></a>IDiaSymbol::get_numberOfColumns
抓取矩陣中的資料行數目。

## <a name="syntax"></a>語法

```C++
HRESULT get_numberOfColumns(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷的指標 `DWORD` ，其中保存矩陣中的資料行數目。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)