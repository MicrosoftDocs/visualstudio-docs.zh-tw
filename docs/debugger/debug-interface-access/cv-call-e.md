---
title: CV_call_e | Microsoft Docs
description: 取得 CV_call_e 列舉型別的參考資訊，其可指定 debug interface access SDK 中函式的呼叫慣例。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 521d5640f001fa0bc190e1869a6568328e864f5a
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728619"
---
# <a name="cv_call_e"></a>CV_call_e
指定函數的呼叫慣例。

> [!NOTE]
> 這裡只會記錄最常見的列舉值。 完整列舉可在 cvconst .h 標頭檔中取得。

## <a name="syntax"></a>Syntax

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

## <a name="elements"></a>元素
CV_CALL_NEAR_C 使用接近的由右至左推送來指定函式呼叫慣例。 呼叫的函式會清除堆疊。

CV_CALL_NEAR_FAST 使用與暫存器接近的左至右推播來指定函式呼叫慣例。 呼叫的函式會使用參數位元組的總和來清除堆疊。

CV_CALL_NEAR_STD 使用接近標準的呼叫（ (由右至左推入) ）來指定函式呼叫慣例。

CV_CALL_NEAR_SYS 使用近端系統呼叫來指定函式呼叫慣例。

CV_CALL_THISCALL 使用 `this` `this` 在 register) 中傳遞的呼叫 (指標，指定函式呼叫慣例。

CV_CALL_CLRCALL 指定 Common Language Runtime (CLR) 所使用的函式呼叫慣例， (也稱為 managed 程式碼呼叫慣例) 。

## <a name="remarks"></a>備註
呼叫 [IDiaSymbol：： get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) 方法時，會傳回此列舉中的值。

## <a name="requirements"></a>規格需求
標頭： cvconst。h

## <a name="see-also"></a>請參閱
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
