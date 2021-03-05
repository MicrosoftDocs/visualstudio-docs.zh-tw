---
description: 抓取旗標，這個旗標會指定函式是否包含使用 longjmp) 命令 (與 setjmp (/cpp/c-runtime-library/reference/setjmp) 命令配對，這些會形成例外狀況處理) 的 C 樣式方法。
title: IDiaSymbol：： get_hasLongJump |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasLongJump method
ms.assetid: 14484cb1-43b0-47a1-a9a8-081b55566886
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1c211e52e1a8e13a88b6c2a2f9404f5d8a67386f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156297"
---
# <a name="idiasymbolget_haslongjump"></a>IDiaSymbol::get_hasLongJump
抓取旗標，這個旗標會指定函式是否包含使用 [longjmp](/cpp/c-runtime-library/reference/longjmp) 命令 (與 [setjmp](/cpp/c-runtime-library/reference/setjmp) 命令配對，而這些會形成例外狀況處理) 的 C 樣式方法。

## <a name="syntax"></a>語法

```C++
HRESULT get_hasLongJump
   BOOL *pFlag
);
```

#### <a name="parameters"></a>參數
 `pFlag`

擴展如果函式 `TRUE` 包含命令，則會傳回 `longjmp` ，否則會傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該屬性不適用於符號。

## <a name="requirements"></a>規格需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本：|DIA SDK v8.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)
- [longjmp](/cpp/c-runtime-library/reference/longjmp)
- [setjmp](/cpp/c-runtime-library/reference/setjmp)
