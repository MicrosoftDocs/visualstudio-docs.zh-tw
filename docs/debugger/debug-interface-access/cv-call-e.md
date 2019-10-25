---
title: CV_call_e | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5deb59d4bbee06e505ba10bf1d4f08b1b06aa62d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745346"
---
# <a name="cv_call_e"></a>CV_call_e
指定函式的呼叫慣例。

> [!NOTE]
> 這裡只記載最常見的列舉值。 完整的列舉可在 cvconst 標頭檔中取得。

## <a name="syntax"></a>語法

```C++
typedef enum CV_call_e {
    CV_CALL_NEAR_C    = 0x00,
    CV_CALL_NEAR_FAST = 0x04,
    CV_CALL_NEAR_STD  = 0x07,
    CV_CALL_NEAR_SYS  = 0x09,
    CV_CALL_THISCALL  = 0x0b,
    CV_CALL_CLRCALL   = 0x16
} CV_call_e;
```

## <a name="elements"></a>項目
CV_CALL_NEAR_C 會使用接近右至左推播來指定函式呼叫慣例。 呼叫函式會清除堆疊。

CV_CALL_NEAR_FAST 會指定函式呼叫慣例，並搭配暫存器使用接近的從左至右推送。 所呼叫的函式會使用參數位元組的總和來清除堆疊。

CV_CALL_NEAR_STD 會使用接近標準的呼叫（由右至左推播）來指定函式呼叫慣例。

CV_CALL_NEAR_SYS 使用 NEAR 系統呼叫來指定函式呼叫慣例。

CV_CALL_THISCALL 會使用 `this` 呼叫（在暫存器中傳遞 `this` 指標）來指定函式呼叫慣例。

CV_CALL_CLRCALL 指定通用語言執行時間（CLR）所使用的函式呼叫慣例（也稱為 managed 程式碼呼叫慣例）。

## <a name="remarks"></a>備註
這個列舉中的值是由呼叫[IDiaSymbol：： get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)方法所傳回。

## <a name="requirements"></a>需求
標頭： cvconst。h

## <a name="see-also"></a>請參閱
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
