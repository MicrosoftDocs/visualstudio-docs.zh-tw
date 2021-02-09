---
title: IDiaSession::symsAreEquiv | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 10aa5f1b086856793fe32512867834848b6f7162
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855015"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
查看兩個符號是否相等。

## <a name="syntax"></a>語法

```C++
HRESULT symsAreEquiv ( 
   IDiaSymbol* symbolA,
   IDiaSymbol* symbolB
);
```

#### <a name="parameters"></a>參數
 `symbolA`

在比較中使用的第一個 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 物件。

 `symbolB`

在比較中使用的第二個 `IDiaSymbol` 物件。

## <a name="return-value"></a>傳回值
 如果符號相等，則會傳回 `S_OK` ; 否則會傳回 `S_FALSE` ，符號不相等。 否則，會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)