---
title: IDiaSymbol::get_hasSetJump | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSetJump method
ms.assetid: 22656206-dccf-40ed-b179-fc016d1b262a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d560cbff64a5134fa58ade4d562cb9fb073af48f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63401525"
---
# <a name="idiasymbolgethassetjump"></a>IDiaSymbol::get_hasSetJump
擷取指定的函式是否包含使用的旗標[setjmp](/cpp/c-runtime-library/reference/setjmp)命令 (搭配[longjmp](/cpp/c-runtime-library/reference/longjmp)命令時，這些形成例外狀況處理的 C 樣式方法)。

## <a name="syntax"></a>語法

```C++
HRESULT get_hasSetJump(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>參數
 `pFlag`

[out]會傳回`TRUE`函數若包含`setjmp`命令; 否則會傳回`FALSE`。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。

> [!NOTE]
> 傳回值為`S_FALSE`表示此屬性不適用於符號。

## <a name="requirements"></a>需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2.h|
|版本:|DIA SDK v8.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)
- [longjmp](/cpp/c-runtime-library/reference/longjmp)
- [setjmp](/cpp/c-runtime-library/reference/setjmp)