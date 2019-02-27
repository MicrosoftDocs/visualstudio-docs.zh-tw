---
title: 'Idiasymbol:: Get_intrinsic |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_intrinsic method
ms.assetid: f969f595-d9f9-48b9-adaa-63a6e4e09575
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9552851917aeb6135d394ac5af8fcf3a5a4b9467
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56645767"
---
# <a name="idiasymbolgetintrinsic"></a>IDiaSymbol::get_intrinsic
擷取指定類別是否為內建類型的旗標。

## <a name="syntax"></a>語法

```C++
HRESULT get_intrinsic( 
   BOOL* pRetVal)
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

[out]會傳回`TRUE`類別是內建函式的型別; 否則會傳回`FALSE`。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。

> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於符號。

## <a name="remarks"></a>備註

## <a name="requirements"></a>需求
 標頭： Dia2.h

 程式庫： diaguids.lib

 DLL: msdia100.dll

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)