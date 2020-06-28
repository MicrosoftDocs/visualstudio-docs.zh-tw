---
title: IDiaSession::findInlineeLines | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: b6822d8b-70d5-470b-8278-3aec4680326c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a03eb23929d3a882b397a8a95f2d9c4c17abf0df
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465808"
---
# <a name="idiasessionfindinlineelines"></a>IDiaSession::findInlineeLines
抓取列舉型別，可讓用戶端逐一查看由指定的父符號直接或間接內嵌之所有函式的行號資訊。

## <a name="syntax"></a>語法

```C++
HRESULT findInlineeLines ( 
   IDiaSymbol*       parent,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>參數
 `parent`

在`IDiaSymbol`代表父系的物件。

 `ppResult`

脫銷保存 `IDiaEnumLineNumbers` 物件，其中包含所抓取的行號清單。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)