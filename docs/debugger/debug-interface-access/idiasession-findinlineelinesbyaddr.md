---
description: IDiaSession：： findInlineeLinesByAddr 會抓取列舉，以允許用戶端逐一查看由指定的父系符號內嵌、直接或間接內嵌之所有函式的行號資訊，並且包含在指定的位址範圍內。
title: IDiaSession::findInlineeLinesByAddr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: bb70e408-eed1-4c9c-b5b1-44323125f48b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 917da4855990844fb6bc0c3fc995174b519b129e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147769"
---
# <a name="idiasessionfindinlineelinesbyaddr"></a>IDiaSession::findInlineeLinesByAddr
抓取列舉，此列舉可讓用戶端逐一查看由指定的父系符號內嵌、直接或間接內嵌之所有函式的行號資訊，並且包含在指定的位址範圍內。

## <a name="syntax"></a>語法

```C++
HRESULT findInlineeLinesByAddr ( 
   IDiaSymbol*           parent,   DWORD                 isect,   DWORD                 offset,   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>參數
 `parent`

在 `IDiaSymbol` 代表父系的物件。

 `isect`

在指定位址的區段元件。

 `offset`

在指定位址的位移元件。

 `length`

在指定要包含在此查詢中的位址範圍（以位元組數為單位）。

 `ppResult`

擴展保存 `IDiaEnumLineNumbers` 物件，其中包含所抓取行號的清單。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
