---
title: IDiaSession::symsAreEquiv | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0253104cf29e86825fadc8c8bd18133e0d3cf593
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839071"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
檢查兩個符號是否相等。

## <a name="syntax"></a>語法

```C++
HRESULT symsAreEquiv ( 
   IDiaSymbol* symbolA,
   IDiaSymbol* symbolB
);
```

#### <a name="parameters"></a>參數
 `symbolA`

[in]第一個[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)用於比較的物件。

 `symbolB`

[in]第二個`IDiaSymbol`用於比較的物件。

## <a name="return-value"></a>傳回值
 如果符號相等，則會傳回`S_OK`; 否則傳回`S_FALSE`，符號不相等。 否則，傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)