---
title: IDiaStackFrame::get_lengthLocals | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_lengthLocals method
ms.assetid: dbc3e544-578a-4f0b-8d20-f21ad4cbb604
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e408f7a6341685394731ea65ceaa926351587a9e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741707"
---
# <a name="idiastackframeget_lengthlocals"></a>IDiaStackFrame::get_lengthLocals
抓取推播于堆疊上的本機變數的位元組數目。

## <a name="syntax"></a>語法

```C++
HRESULT get_lengthLocals ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回本機變數的位元組數目。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 如果不支援此屬性，則會傳回 `S_FALSE`。 否則會傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)