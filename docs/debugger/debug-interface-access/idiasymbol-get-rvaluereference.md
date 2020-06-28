---
title: IDiaSymbol：： get_RValueReference |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_RValueReference method
ms.assetid: c6c8c543-253e-4c23-a939-3e66f3db0ee2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8123ca0a9679a46e8e411d817f42ae8497f3ef3
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85462403"
---
# <a name="idiasymbolget_rvaluereference"></a>IDiaSymbol::get_RValueReference
抓取指定指標類型是否為右值參考的旗標。 當[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)設定為指標類型時，請使用。

## <a name="syntax"></a>語法

```C++
HRESULT get_RValueReference (
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷`TRUE`如果指標是右值參考，則傳回，否則傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示此屬性無法用於符號。

## <a name="remarks"></a>備註

## <a name="requirements"></a>需求
 標頭： Dia2。h

 程式庫： diaguids

 DLL： msdia100.dll

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)