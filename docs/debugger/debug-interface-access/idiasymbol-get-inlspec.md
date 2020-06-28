---
title: IDiaSymbol：： get_InlSpec |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_InlSpec method
ms.assetid: 30af6a2f-be84-429e-a96a-d0f9ed9343fb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 676ae888de9cbf6a32e77571848d84a0632d0cc0
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463565"
---
# <a name="idiasymbolget_inlspec"></a>IDiaSymbol::get_InlSpec
此函式會抓取旗標，指出函式是否標示為內嵌（使用其中一個[內嵌、__inline \_ _forceinline](/cpp/cpp/inline-functions-cpp)屬性）。

## <a name="syntax"></a>語法

```C++
HRESULT get_inlSpec(
   BOOL *pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷如果函式 `TRUE` 標記為內嵌，則傳回，否則傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該屬性不適用於符號。

## <a name="requirements"></a>需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本：|DIA SDK v8.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [內嵌、__inline、 \_ _forceinline](/cpp/cpp/inline-functions-cpp)