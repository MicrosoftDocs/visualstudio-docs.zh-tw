---
description: 此函式會抓取旗標，指出是否已使用其中一個內嵌、_inline __forceinline) 屬性) ，將函數標記為內嵌 (。
title: IDiaSymbol：： get_InlSpec |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_InlSpec method
ms.assetid: 30af6a2f-be84-429e-a96a-d0f9ed9343fb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f727e83d067fed37698eb750bb39309a9454535a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160866"
---
# <a name="idiasymbolget_inlspec"></a>IDiaSymbol::get_InlSpec
此函式會抓取旗標，指出是否已使用其中一個 [內嵌、__inline \_ _forceinline](/cpp/cpp/inline-functions-cpp) 屬性) ，將函數標記為內嵌 (。

## <a name="syntax"></a>語法

```C++
HRESULT get_inlSpec(
   BOOL *pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展如果函式 `TRUE` 標記為內嵌，則傳回，否則傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
 如果成功， `S_OK` 則傳回; 否則傳回 `S_FALSE` 錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該屬性不適用於符號。

## <a name="requirements"></a>規格需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本：|DIA SDK v8.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [內嵌、__inline、 \_ _forceinline](/cpp/cpp/inline-functions-cpp)
