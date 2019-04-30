---
title: IDiaSession::findLinesByRVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByRVA method
ms.assetid: 06f53b0b-b5b4-42cf-9252-dcee0dbe2d71
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4316bfa423392a98946fc0bb86af2f2e9836aba2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62827678"
---
# <a name="idiasessionfindlinesbyrva"></a>IDiaSession::findLinesByRVA
擷取指定的編譯模組中的行，其中包含指定相對虛擬位址 (RVA)。

## <a name="syntax"></a>語法

```C++
HRESULT findLinesByRVA ( 
    DWORD                 rva,
    DWORD                 length,
    IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>參數
`rva`

[in]RVA 為指定的位址。

`length`

[in]指定的位址範圍，以涵蓋此查詢使用的位元組數目。

`ppResult`

[out]傳回[IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)物件，其中包含一份所有列的數字，涵蓋的指定的位址範圍。

## <a name="return-value"></a>傳回值
如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="example"></a>範例
此範例示範會取得所有包含在指定的函式使用函式的相對虛擬位址和長度的行號的功能。

```C++
IDiaEnumLineNumbers* GetLineNumbersByRVA(IDiaSymbol *pFunc, IDiaSession *pSession)
{
    IDiaEnumLineNumbers* pEnum = NULL;
    DWORD                rva;
    ULONGLONG            length;

    if (pFunc->get_relativeVirtualAddress ( &rva ) == S_OK)
    {
        pFunc->get_length ( &length );
        pSession->findLinesByRVA( rva, static_cast<DWORD>( length ), &pEnum );
    }
    return(pEnum);
}
```

## <a name="see-also"></a>另請參閱
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
