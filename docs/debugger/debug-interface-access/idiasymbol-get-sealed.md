---
title: IDiaSymbol：： get_sealed |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_sealed method
ms.assetid: cd1fef1f-47de-47c7-885f-f6f0a9a07d8c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b1f826c4dfcc8f000b37144b28dfcb8cf503a87
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85462050"
---
# <a name="idiasymbolget_sealed"></a>IDiaSymbol::get_sealed
抓取指定類別或方法是否為密封的旗標。

## <a name="syntax"></a>語法

```C++
HRESULT get_sealed( 
   BOOL* pRetVal)
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷`TRUE`如果類別或方法已密封，則傳回，否則傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示此屬性無法用於符號。

## <a name="remarks"></a>備註
 密封類別不能當做基底類別使用。 密封的方法無法覆寫。

## <a name="requirements"></a>需求
 標頭： Dia2。h

 程式庫： diaguids

 DLL： msdia100.dll

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)