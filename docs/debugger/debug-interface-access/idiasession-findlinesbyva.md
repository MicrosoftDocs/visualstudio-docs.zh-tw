---
title: IDiaSession::findLinesByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByVA method
ms.assetid: f647eee9-a73c-483b-9fe9-21f42e560a7b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5e39793e2060daebf93759feb9c64622a9cf880
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465577"
---
# <a name="idiasessionfindlinesbyva"></a>IDiaSession::findLinesByVA
抓取指定虛擬位址（VA）範圍內所包含之行的行號資訊。

## <a name="syntax"></a>語法

```C++
HRESULT findLinesByVA (
    ULONGLONG             va,
    DWORD                 length,
    IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>參數
`va`

在將位址指定為 VA。

`length`

在指定要與此查詢一併涵蓋之位址範圍的位元組數目。

`ppResult`

脫銷傳回[IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)物件，其中包含涵蓋指定之位址範圍的所有行號清單。

## <a name="example"></a>範例
這個範例會顯示函式，該函式會使用函式的虛擬位址和長度，取得函式中包含的所有行號。

```C++
IDiaEnumLineNumbers *GetLineNumbersByVA(IDiaSymbol *pFunc, IDiaSession *pSession)
{
    IDiaEnumLineNumbers* pEnum = NULL;
    ULONGLONG            va;
    ULONGLONG            length;

    if (pFunc->get_virtualAddress ( &va ) == S_OK)
    {
        pFunc->get_length( &length );
        pSession->findLinesByVA( va, static_cast<DWORD>( length ), &pEnum );
    }
    return(pEnum);
}
```

## <a name="see-also"></a>另請參閱
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
