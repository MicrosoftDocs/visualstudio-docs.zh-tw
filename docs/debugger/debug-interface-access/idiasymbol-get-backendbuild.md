---
description: 抓取編譯器的後端組建編號。
title: IDiaSymbol：： get_backEndBuild |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_backEndBuild method
ms.assetid: 423af497-9294-438e-92b4-456c6f56dc56
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 02864e046e5227d22e6c07fb70efad80b53e3689
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156493"
---
# <a name="idiasymbolget_backendbuild"></a>IDiaSymbol::get_backEndBuild
抓取編譯器的後端組建編號。

## <a name="syntax"></a>語法

```C++
HRESULT get_backEndBuild ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展傳回後端組建編號。 請參閱＜備註＞。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該屬性不適用於符號。

## <a name="remarks"></a>備註
 編譯器通常是由兩個主要元素組成：前端 (剖析器) ，其會將原始程式碼剖析成中繼格式，而後端 (程式碼產生器) ，這會將中繼格式轉換成元件。 前端與後端的版本不同，不是罕見的。

 前端或後端版本號碼由三個部分組成： \<major> ... \<minor> \<build> ，其中 \<major> 是主要版本號碼， \<minor> 是次要版本號碼，而 \<build> 是組建編號。 例如 13.10.3077。

## <a name="requirements"></a>規格需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本：|DIA SDK v7.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
