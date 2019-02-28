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
ms.openlocfilehash: ec5fea99994b891250dad85cfc43320848df98f9
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56602750"
---
# <a name="cvcalle"></a>CV_call_e
指定函式的呼叫慣例。

> [!NOTE]
> 只有最常見的列舉值記載於此。 完整的列舉型別適用於 cvconst.h 標頭檔。

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
CV_CALL_NEAR_C 指定使用幾近的由右至左推入的函式呼叫慣例。 呼叫的函式會清除堆疊。

CV_CALL_NEAR_FAST 指定函式呼叫慣例，使用幾近左到右推送以註冊。 呼叫的函式會清除堆疊中使用參數的位元組總數。

CV_CALL_NEAR_STD 指定使用近乎標準呼叫 （由右至左推入） 的函式呼叫慣例。

使用 near 系統函式呼叫慣例 CV_CALL_NEAR_SYS 指定呼叫。

函式呼叫慣例，使用時，指定 CV_CALL_THISCALL`this`呼叫 (`this`暫存器中傳遞的指標)。

CV_CALL_CLRCALL 指定使用的 Common Language Runtime (CLR) （也稱為 managed 程式碼呼叫慣例） 的函式呼叫慣例。

## <a name="remarks"></a>備註
這個列舉型別中的值會傳回呼叫[idiasymbol:: Get_callingconvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)方法。

## <a name="requirements"></a>需求
標頭： cvconst.h

## <a name="see-also"></a>請參閱
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
