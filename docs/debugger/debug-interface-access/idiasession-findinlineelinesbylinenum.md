---
title: IDiaSession::findInlineeLinesByLinenum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: cf32ae7c-a0c8-4800-bc8f-d64fdd15fb06
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac7f2299dcfbef53c510c9e9689f92cde2132974
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465794"
---
# <a name="idiasessionfindinlineelinesbylinenum"></a>IDiaSession::findInlineeLinesByLinenum
抓取列舉型別，可讓用戶端逐一查看指定的原始程式檔和行號中，直接或間接內嵌之所有函式的行號資訊。

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

在[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，表示要在其中搜尋行號的編譯模組。 這個參數不可以是 `NULL`。

 `file`

在[IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)物件，表示要在其中搜尋的來源檔案。 這個參數不可以是 `NULL`。

 `linenum`

在指定以一為基礎的行號。

> [!NOTE]
> 您不能使用零來指定所有行（使用[IDiaSession：： findLines](../../debugger/debug-interface-access/idiasession-findlines.md)方法來尋找所有行）。

 `column`

在指定資料行編號。 使用零來指定所有資料行。 「資料行」是一行中的位元組位移。

 `ppResult`

脫銷傳回[IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)物件，其中包含已抓取的行號清單。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)