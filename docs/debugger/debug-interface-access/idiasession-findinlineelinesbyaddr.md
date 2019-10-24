---
title: IDiaSession::findInlineeLinesByAddr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: bb70e408-eed1-4c9c-b5b1-44323125f48b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 496f6b569b3ac02c625ddf18406b78fdb1687be2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742226"
---
# <a name="idiasessionfindinlineelinesbyaddr"></a>IDiaSession::findInlineeLinesByAddr
抓取列舉型別，可讓用戶端逐一查看由指定的父符號內嵌、直接或間接內嵌之所有函式的行號資訊，並包含在指定的位址範圍內。

## <a name="syntax"></a>語法

```C++
HRESULT findInlineeLinesByAddr ( 
   IDiaSymbol*           parent,   DWORD                 isect,   DWORD                 offset,   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>參數
 `parent`

在代表父系的 `IDiaSymbol` 物件。

 `isect`

在指定位址的區段元件。

 `offset`

在指定位址的位移元件。

 `length`

在指定要與此查詢一併涵蓋的位址範圍（以位元組數為單位）。

 `ppResult`

脫銷保存 `IDiaEnumLineNumbers` 物件，其中包含所抓取的行號清單。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)