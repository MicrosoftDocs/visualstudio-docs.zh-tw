---
title: 'Idiasymbol:: Get_notreached |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_notReached method
ms.assetid: e44ba922-6cda-40c2-9b62-44e5a8628e63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d448fe9c8eb3379d4d66bbc174626a3c3998a737
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639306"
---
# <a name="idiasymbolgetnotreached"></a>IDiaSymbol::get_notReached
擷取旗標，指定是否函式或標籤永遠不會到達。

## <a name="syntax"></a>語法

```C++
HRESULT get_notReached(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>參數
 pFlag

[out]會傳回`TRUE`函式或標籤永遠不會達到; 否則會傳回`FALSE`。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。

> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於符號。

## <a name="requirements"></a>需求

|需求|說明|
|-----------------|-----------------|
|標頭：|dia2.h|
|版本:|DIA SDK v8.0|

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)