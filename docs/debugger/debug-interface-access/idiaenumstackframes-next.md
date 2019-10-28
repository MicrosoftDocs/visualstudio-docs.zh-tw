---
title: IDiaEnumStackFrames::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffde40e221823d9656c4b6414b14067ac9d0537a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744032"
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
從列舉序列中抓取指定的堆疊框架元素數目。

## <a name="syntax"></a>語法

```C++
HRESULT Next( 
   ULONG             celt,
   IDiaStackFrame**  rgelt,
   ULONG*            pceltFetched
);
```

#### <a name="parameters"></a>參數
 celt

在列舉值中要抓取的 stackframe 元素數目。

 rgelt

脫銷要以要求的[IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)物件填入的陣列。

 pceltFetched

脫銷傳回已提取列舉值中的堆疊框架元素數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 如果沒有其他堆疊框架，則傳回 `S_FALSE`。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)