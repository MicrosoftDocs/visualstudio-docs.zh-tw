---
description: 抓取列舉，可讓用戶端逐一查看在指定的原始程式檔和行號中，直接或間接內嵌的所有函式的行號資訊。
title: IDiaSession::findInlineeLinesByLinenum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: cf32ae7c-a0c8-4800-bc8f-d64fdd15fb06
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 130c270e0be0e38768018467e117361c9befd796
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147762"
---
# <a name="idiasessionfindinlineelinesbylinenum"></a>IDiaSession::findInlineeLinesByLinenum
抓取列舉，可讓用戶端逐一查看在指定的原始程式檔和行號中，直接或間接內嵌的所有函式的行號資訊。

## <a name="syntax"></a>語法

```C++
HRESULT findInlineeLinesByVA ( 
   IDiaSymbol*           compiland,
   IDiaSourceFile*       file,
   DWORD                 linenum,
   DWORD                 column,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>參數
 `compiland`

在 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 物件，代表要在其中搜尋行號的編譯單位。 這個參數不可以是 `NULL`。

 `file`

在 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) 物件，代表要在其中搜尋的原始程式檔。 這個參數不可以是 `NULL`。

 `linenum`

在指定以一個為基礎的行號。

> [!NOTE]
> 您無法使用零來指定所有的行 (使用 [IDiaSession：： findLines](../../debugger/debug-interface-access/idiasession-findlines.md) 方法來尋找) 的所有行。

 `column`

在指定資料行編號。 使用零來指定所有資料行。 資料行是一行的位元組位移。

 `ppResult`

擴展傳回 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) 物件，其中包含已取出行號的清單。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
