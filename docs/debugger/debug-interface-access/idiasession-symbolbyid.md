---
title: IDiaSession::symbolById | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symbolById method
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01c2470be57616dcb026c3f5f29e3b2ab2a11a4e
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465388"
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
依其唯一識別碼抓取符號。

## <a name="syntax"></a>語法

```C++
HRESULT symbolById (
    DWORD        id,
    IDiaSymbol** ppSymbol
);
```

#### <a name="parameters"></a>參數
`id`

在唯一識別碼。

`ppSymbol`

脫銷傳回代表所抓取符號的[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件。

## <a name="return-value"></a>傳回值
如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="remarks"></a>備註
指定的識別碼是 DIA SDK 在內部使用的唯一值，讓所有符號都是唯一的。

例如，您可以使用這個方法來抓取代表另一個符號類型的符號（請參閱範例）。

## <a name="example"></a>範例
這個範例會抓取代表另一個符號之類型的[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 。 這個範例會示範如何 `symbolById` 在會話中使用方法。 較簡單的方法是呼叫[IDiaSymbol：： get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)方法，直接取得類型符號。

```C++
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)
{
    IDiaSymbol *pTypeSymbol = NULL;
    if (pSymbol != NULL && pSession != NULL)
    {
        DWORD symbolTypeId;
        pSymbol->get_typeId(&symbolTypeId);
        pSession->symbolById(symbolTypeId, &pTypeSymbol);
    }
    return(pTypeSymbol);
}
```

## <a name="see-also"></a>另請參閱
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
