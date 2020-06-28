---
title: IDiaSession::findInlineeLinesByRVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 7a74d5ee-0dbf-47c0-92b4-47ec03b13ce9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9469415682d7347aa3d51ee09878e31e28e85f62
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465717"
---
# <a name="idiasessionfindinlineelinesbyrva"></a>IDiaSession::findInlineeLinesByRVA
抓取列舉型別，可讓用戶端逐一查看由指定的父符號內嵌、直接或間接內嵌之所有函式的行號資訊，並包含在指定的相對虛擬位址（RVA）內。

## <a name="syntax"></a>語法

```C++
HRESULT findInlineeLinesByRVA ( 
   IDiaSymbol*           parent,
   DWORD                 rva,
   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>參數
 `parent`

在`IDiaSymbol`代表父系的物件。

 `rva`

在將位址指定為 RVA。

 `length`

在指定要與此查詢一併涵蓋的位址範圍（以位元組數為單位）。

 `ppResult`

脫銷保存 `IDiaEnumLineNumbers` 物件，其中包含所抓取的行號清單。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)