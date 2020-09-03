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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85462403"
---
# <a name="idiasymbolget_rvaluereference"></a>IDiaSymbol::get_RValueReference
抓取旗標，指定指標類型是否為右值參考。 當 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md) 設定為指標類型時使用。

## <a name="syntax"></a>語法

```C++
HRESULT get_RValueReference (
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展 `TRUE` 如果指標是右值參考，則傳回，否則傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。

## <a name="remarks"></a>備註

## <a name="requirements"></a>需求
 標頭： Dia2。h

 程式庫： diaguids .lib

 DLL： msdia100.dll

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)