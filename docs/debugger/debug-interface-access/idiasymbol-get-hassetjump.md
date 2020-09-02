---
title: IDiaSymbol::get_hasSetJump | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 353247c494b803871a9c64126545e11be39bfcae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85463635"
---
# <a name="idiasymbolget_hassetjump"></a>IDiaSymbol::get_hasSetJump
抓取旗標，這個旗標會指定函式是否包含使用 [setjmp](/cpp/c-runtime-library/reference/setjmp) 命令 (與 [longjmp](/cpp/c-runtime-library/reference/longjmp) 命令配對，而這些會形成例外狀況處理) 的 C 樣式方法。

## <a name="syntax"></a>語法

```C++
HRESULT get_hasSetJump(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>參數
 `pFlag`

擴展如果函式 `TRUE` 包含命令，則會傳回 `setjmp` ，否則會傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
 如果成功， `S_OK` 則傳回; 否則傳回 `S_FALSE` 錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。

## <a name="requirements"></a>需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本：|DIA SDK v8.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)
- [longjmp](/cpp/c-runtime-library/reference/longjmp)
- [setjmp](/cpp/c-runtime-library/reference/setjmp)