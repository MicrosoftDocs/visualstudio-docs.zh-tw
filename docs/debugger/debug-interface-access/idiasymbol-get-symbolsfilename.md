---
title: IDiaSymbol::get_symbolsFileName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_symbolsFileName method
ms.assetid: c1aa39ee-d645-431e-bf5f-0640c0998934
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eced26fe8316966807dab68c5361535cb551f5d1
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "64796087"
---
# <a name="idiasymbolgetsymbolsfilename"></a>IDiaSymbol::get_symbolsFileName
擷取已載入符號來源檔案的名稱。

## <a name="syntax"></a>語法

```C++
HRESULT get_symbolsFileName ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

[out]傳回已載入符號來源檔案的名稱。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。

> [!NOTE]
> 傳回值為`S_FALSE`表示此屬性不適用於符號。

## <a name="remarks"></a>備註
 這個屬性是僅適用於具有符號[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)的值`SymTagExe`也具有全域範圍。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)