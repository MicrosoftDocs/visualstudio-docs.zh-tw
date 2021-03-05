---
description: 抓取編譯單位的符號參考，以提供影像文字的位元組。
title: IDiaLineNumber：： get_compiland |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_compiland method
ms.assetid: c476d0b8-c473-47eb-96f5-c4e8f577b1c9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2700ffb00c14a0f9f62f274157ffadecb0abee26
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157592"
---
# <a name="idialinenumberget_compiland"></a>IDiaLineNumber::get_compiland
抓取編譯單位的符號參考，以提供影像文字的位元組。

## <a name="syntax"></a>語法

```C++
HRESULT get_compiland ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>參數
 pRetVal

擴展傳回提供影像文字位元組之編譯單位的 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援這個屬性，則傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
