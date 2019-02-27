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
ms.openlocfilehash: f9cf220c65cf11836e64a7e1f4c0142c89669f4b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619442"
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
擷取列舉型別序列中的堆疊框架項目指定的數目。

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

[in]要擷取列舉值中的 stackframe 元素數目。

 rgelt

[out]陣列，是要填入所要求[IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)物件。

 pceltFetched

[out]擷取列舉值中傳回的堆疊框架項目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 傳回`S_FALSE`有沒有更多的堆疊框架。 否則會傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)