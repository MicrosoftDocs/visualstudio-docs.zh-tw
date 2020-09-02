---
title: IDiaSession：： findSymbolByToken |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByToken method
ms.assetid: 3c92149c-6eef-454f-86be-66e89557b9e6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2656cd8e1b509dbfbd3651bf850341c55702d60d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85465556"
---
# <a name="idiasessionfindsymbolbytoken"></a>IDiaSession::findSymbolByToken
抓取包含指定之元資料標記的符號。

## <a name="syntax"></a>語法

```C++
HRESULT findSymbolByToken ( 
   ULONG        token,
   SymTagEnum   symtag,
   IDiaSymbol** ppSymbol
);
```

#### <a name="parameters"></a>參數
 `token`

在指定權杖。

 `symtag`

在要尋找的符號類型。 值取自 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md) 列舉。

 `ppSymbol`

擴展傳回代表已抓取符號的 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="example"></a>範例

```C++
IDiaSymbol* pFunc;
pSession->findSymbolByToken( token, SymTagFunction, &pFunc );
```

## <a name="see-also"></a>另請參閱
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)