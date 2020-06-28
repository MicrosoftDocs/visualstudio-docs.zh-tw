---
title: IDiaEnumSymbols：： Next |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Next method
ms.assetid: bfe5fe27-6a84-4392-910f-e325146d7552
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 110cacc241a733289b8cdce60c2d64c6fdf298e2
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467726"
---
# <a name="idiaenumsymbolsnext"></a>IDiaEnumSymbols::Next
抓取列舉序列中指定數目的符號。

## <a name="syntax"></a>語法

```C++
HRESULT Next ( 
   ULONG        celt,
   IDiaSymbol** rgelt,
   ULONG*       pceltFetched
);
```

#### <a name="parameters"></a>參數
 celt

在列舉值中要抓取的符號數目。

 rgelt

脫銷要填入的陣列，其中包含代表所需符號的[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件。

 pceltFetched

脫銷傳回已提取枚舉器中的符號數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 如果沒有其他符號，則傳回 `S_FALSE` 。 否則會傳回錯誤碼。

## <a name="example"></a>範例

```C++
IDiaEnumSymbols* pEnum
CComPtr< IDiaSymbol> pSym;
DWORD celt;
pEnum->Next( 1, &pSym, &celt );
```

## <a name="see-also"></a>另請參閱
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)