---
title: IDiaSymbol::findInlineFramesByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 54295d3e-bbb6-4c10-ab9d-adcfc22b1f71
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffe73d910520966f49e7cc345cd5abbf18a9d32a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464454"
---
# <a name="idiasymbolfindinlineframesbyva"></a>IDiaSymbol::findInlineFramesByVA
抓取列舉，可讓用戶端逐一查看指定虛擬位址的所有內嵌框架 (VA) 。

## <a name="syntax"></a>語法

```C++
HRESULT findInlineFramesByVA ( 
   ULONGLONG         va,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>參數
 `va`

在將位址指定為 VA。

 `ppResult`

擴展保存 `IDiaEnumSymbols` 物件，其中包含所抓取的框架清單。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)