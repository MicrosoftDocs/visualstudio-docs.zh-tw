---
description: 從列舉序列中抓取指定數目的堆疊框架元素。
title: IDiaEnumStackFrames::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0cee13aa9e26de77cf22cf7a51011a567cb14c25
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159157"
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
從列舉序列中抓取指定數目的堆疊框架元素。

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

在要抓取的列舉值中 stackframe 元素的數目。

 rgelt

擴展要以要求的 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) 物件填入的陣列。

 pceltFetched

擴展傳回已提取枚舉器中堆疊框架專案的數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果沒有其他堆疊框架，則會傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
