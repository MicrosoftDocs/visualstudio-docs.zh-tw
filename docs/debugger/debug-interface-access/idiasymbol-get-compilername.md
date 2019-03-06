---
title: IDiaSymbol::get_compilerName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_compilerName method
ms.assetid: 66eaaf72-68d4-40ee-b132-97bea9fe395c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94a054446332c60236ead4a3f034f6bc001a7feb
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56621756"
---
# <a name="idiasymbolgetcompilername"></a>IDiaSymbol::get_compilerName
傳回的名稱，用來產生的編譯器[編譯模組](../../debugger/debug-interface-access/compiland.md)。

## <a name="syntax"></a>語法

```C++
HRESULT get_compilerName (
   BSTR *pName
);
```

#### <a name="parameters"></a>參數
 `pName` BSTR，其中會包含編譯器的 Unicode 名稱的指標。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。

> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於符號。

## <a name="remarks"></a>備註

## <a name="requirements"></a>需求

|需求|說明|
|-----------------|-----------------|
|標頭：|dia2.h|
|版本:|DIA SDK v8.0|

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)