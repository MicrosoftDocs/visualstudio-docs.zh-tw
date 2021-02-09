---
title: IDiaSymbol：： get_noInline |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_noInline method
ms.assetid: 5c610b78-f1a3-494a-acf8-c42b97935be1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b3ac08460995cbaec149c5dda9ffc4c1e3e5bfbf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862959"
---
# <a name="idiasymbolget_noinline"></a>IDiaSymbol::get_noInline
抓取旗標，這個旗標會指定是否使用 [noinline](/cpp/cpp/noinline) 屬性) 將函式標示為非內嵌 (。

## <a name="syntax"></a>語法

```C++
HRESULT get_noInline(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>參數
 `pFlag`

擴展 `TRUE` 如果函數具有屬性，則傳回 `noinline` ，否則傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。

## <a name="requirements"></a>規格需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本：|DIA SDK v8.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [noinline](/cpp/cpp/noinline)