---
title: IDiaStackFrame::get_maxStack | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_maxStack method
ms.assetid: 6352e972-7105-4d0e-aeba-b8fc16d62dec
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9640fa8f82c7bb87990c97ef7916e7323943ece
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741641"
---
# <a name="idiastackframeget_maxstack"></a>IDiaStackFrame::get_maxStack
抓取框架中堆疊推送的最大位元組數目。

## <a name="syntax"></a>語法

```C++
HRESULT get_maxStack ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回堆疊上推送的最大位元組數目。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 如果不支援此屬性，則會傳回 `S_FALSE`。 否則會傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)