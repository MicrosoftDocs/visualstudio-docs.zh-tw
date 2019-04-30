---
title: 'Idiaenumsymbols:: Next |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: ef151b369c18863b8a87944cdbf69fed9aeb0840
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833385"
---
# <a name="idiaenumsymbolsnext"></a>IDiaEnumSymbols::Next
擷取指定的列舉型別序列中的符號數。

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

[in]要擷取列舉值中的符號數目。

 rgelt

[out]陣列，其中是要在以填滿[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，代表所需的符號。

 pceltFetched

[out]擷取列舉值中傳回符號的數。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 傳回`S_FALSE`有沒有更多的符號。 否則會傳回錯誤碼。

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