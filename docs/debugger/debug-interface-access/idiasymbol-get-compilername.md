---
description: 傳回用來產生編譯單位) 之編譯器的名稱。
title: IDiaSymbol::get_compilerName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_compilerName method
ms.assetid: 66eaaf72-68d4-40ee-b132-97bea9fe395c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 27f59110696a12423b9ada1001bcbce8c84d7b5d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162197"
---
# <a name="idiasymbolget_compilername"></a>IDiaSymbol::get_compilerName
傳回用來產生 [編譯單位](../../debugger/debug-interface-access/compiland.md)之編譯器的名稱。

## <a name="syntax"></a>語法

```C++
HRESULT get_compilerName (
   BSTR *pName
);
```

#### <a name="parameters"></a>參數
 `pName` 包含編譯器的 Unicode 名稱之 BSTR 的指標。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。

## <a name="remarks"></a>備註

## <a name="requirements"></a>需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本：|DIA SDK v8.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
