---
description: 抓取值，指出函式是否使用堆疊框架執行階段錯誤檢查進行編譯。 這是/RTCs 旗標。
title: IDiaSymbol：： get_isRTCs |Microsoft Docs
ms.date: 04/27/2021
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isRTCs method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9a297abe6326af6f04058e6095f59f880f526adb
ms.sourcegitcommit: 30c404655fb83ea28f96ab1edb1c09b4d8d7eec4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2021
ms.locfileid: "108217226"
---
# <a name="idiasymbolget_isrtcs"></a>IDiaSymbol：： get_isRTCs

傳回值，這個值會指出函式是否使用堆疊框架執行階段錯誤檢查進行編譯。 這是/RTCs 旗標。

## <a name="syntax"></a>語法

```C++
HRESULT get_isRTCs ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數

 `pRetVal`

擴展布林值的指標，指定函式是否使用堆疊框架執行階段錯誤檢查進行編譯。

## <a name="return-value"></a>傳回值

 如果成功， `S_OK` 則傳回; 否則傳回 `S_FALSE` 錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。

## <a name="remarks"></a>備註

從 Visual Studio 2019 16.10 Preview 2 版開始支援此方法。

## <a name="requirements"></a>規格需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本：|DIA SDK v7.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
