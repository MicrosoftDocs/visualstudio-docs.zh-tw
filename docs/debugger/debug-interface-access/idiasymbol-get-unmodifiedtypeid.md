---
title: IDiaSymbol::get_unmodifiedTypeId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4f7fc73c-f524-4d7a-b378-a9ab99a96104
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6205bf2a80f362d803b5f5e23397a5578ddc2b3
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461585"
---
# <a name="idiasymbolget_unmodifiedtypeid"></a>IDiaSymbol::get_unmodifiedTypeId
抓取原始（未修改）類型的識別碼。

## <a name="syntax"></a>語法

```C++
HRESULT get_unmodifiedTypeId(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷持有識別碼之的指標 `DWORD` 。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)