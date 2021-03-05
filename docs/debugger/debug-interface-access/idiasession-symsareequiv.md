---
description: 查看兩個符號是否相等。
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
ms.openlocfilehash: c5f887b13195bdde133c4bca845291b1255b99ea
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156983"
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
