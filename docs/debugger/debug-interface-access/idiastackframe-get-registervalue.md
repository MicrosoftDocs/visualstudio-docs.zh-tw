---
title: IDiaStackFrame::get_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_registerValue method
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a819293863b658f6e12609b2c1cd83c37532e02d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832101"
---
# <a name="idiastackframegetregistervalue"></a>IDiaStackFrame::get_registerValue
擷取的值指定的暫存器儲存在堆疊框架中。

## <a name="syntax"></a>語法

```C++
HRESULT get_registerValue(
   ULONG      registerIndex,
   ULONGLONG *pRetVal
);
```

#### <a name="parameters"></a>參數
 `registerIndex`

[in]其中一個[CV_HREG_e 列舉](../../debugger/debug-interface-access/cv-hreg-e.md)列舉值。

 `pRetVal`

[out]在登錄中儲存的值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`，否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [CV_HREG_e 列舉](../../debugger/debug-interface-access/cv-hreg-e.md)