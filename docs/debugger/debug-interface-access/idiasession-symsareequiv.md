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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe609d53571e6ffcd8e18919f0351e29c0329b46
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85465360"
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