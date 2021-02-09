---
title: IDiaSession：： findLines |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLines method
ms.assetid: d6e84916-fd55-457e-b057-57f97b51fe73
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6f2949eaca7e6f3a18a121e7b92ecb5db88a2156
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855155"
---
# <a name="idiasessionfindlines"></a>IDiaSession::findLines
抓取指定編譯單位和原始程式檔識別碼內的行號。

## <a name="syntax"></a>語法

```C++
HRESULT findLines ( 
   IDiaSymbol*           compiland,
   IDiaSourceFile*       file,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>參數
 `compiland`

在代表編譯單位的 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 物件。 您可以使用此介面作為內容，以搜尋行號。

 `file`

在 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) 物件，代表要在其中搜尋行號的原始程式檔。

 `ppResult`

擴展傳回 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) 物件，其中包含已抓取行號的清單。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)