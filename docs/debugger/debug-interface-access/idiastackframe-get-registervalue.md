---
description: 抓取儲存在堆疊框架中的指定暫存器值。
title: IDiaStackFrame::get_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_registerValue method
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 92ada384d6e231a33dc2b1bbccfafa1e790f1c9c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147433"
---
# <a name="idiastackframeget_registervalue"></a>IDiaStackFrame::get_registerValue
抓取儲存在堆疊框架中的指定暫存器值。

## <a name="syntax"></a>語法

```C++
HRESULT get_registerValue(
   ULONG      registerIndex,
   ULONGLONG *pRetVal
);
```

#### <a name="parameters"></a>參數
 `registerIndex`

在其中一個 [CV_HREG_e 列舉](../../debugger/debug-interface-access/cv-hreg-e.md) 列舉值。

 `pRetVal`

擴展儲存在暫存器中的值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [CV_HREG_e 列舉](../../debugger/debug-interface-access/cv-hreg-e.md)
