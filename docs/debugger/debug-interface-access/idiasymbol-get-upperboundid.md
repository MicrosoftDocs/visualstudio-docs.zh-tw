---
title: IDiaSymbol：： get_upperBoundId |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_upperBoundId method
ms.assetid: ddfa1617-bd0f-4187-ba77-a225bab93a95
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d573f54a6264562c02960448768a8409fcc5e5a
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461543"
---
# <a name="idiasymbolget_upperboundid"></a>IDiaSymbol::get_upperBoundId
抓取 FORTRAN 陣列維度上限的符號識別碼。

## <a name="syntax"></a>語法

```C++
HRESULT get_upperBoundId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`
- [out，]傳回代表 FORTRAN 陣列維度上限的符號識別碼。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示此屬性無法用於符號。

## <a name="remarks"></a>備註
 識別碼是 DIA SDK 所建立的唯一值，用來將所有符號標記為唯一。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)