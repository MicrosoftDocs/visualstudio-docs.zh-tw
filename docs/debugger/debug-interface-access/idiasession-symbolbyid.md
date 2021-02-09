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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 423bf9a1c6d816d17bb36be6a4a84820617234ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864079"
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

擴展傳回代表已抓取符號的 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 物件。

## <a name="return-value"></a>傳回值
如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
指定的識別碼是唯一的值，由 DIA SDK 在內部使用，讓所有符號都是唯一的。

例如，您可以使用這個方法來取得代表另一個符號類型的符號 (請參閱範例) 。

## <a name="example"></a>範例
此範例會抓取代表另一個符號類型的 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 。 此範例顯示如何 `symbolById` 在會話中使用方法。 更簡單的方法是呼叫 [IDiaSymbol：： get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) 方法來直接取出型別符號。

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
