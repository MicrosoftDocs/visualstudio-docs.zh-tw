---
title: IDiaSymbol::get_type | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_type method
ms.assetid: 1c6a4176-dd4e-4c22-8b8f-0e559fc078ba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 738d3045c524700e803fe82c8902d4f1b77948b5
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461743"
---
# <a name="idiasymbolget_type"></a>IDiaSymbol::get_type
抓取表示此符號之類型的符號。

## <a name="syntax"></a>語法

```C++
HRESULT get_type (
    IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>參數
`pRetVal`

脫銷傳回代表這個符號類型的[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件。

## <a name="return-value"></a>傳回值
如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示此屬性無法用於符號。

## <a name="remarks"></a>備註
若要判斷符號的類型，您必須呼叫這個方法，並檢查產生的[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件。 請注意，符號可能沒有類型。 例如，結構的名稱沒有類型，但它可能會有子符號（使用[IDiaSymbol：： findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)方法來檢查這些子系）。

## <a name="example"></a>範例

```C++
IDiaSymbol*         pType;
CComPtr<IDiaSymbol> pBaseType;
if (SUCCEEDED(pType->get_type( &pBaseType ))) {
    BasicType btBaseType;
    if (SUCCEEDED(pBaseType->get_baseType((DWORD *)&btBaseType))) {
        // Do something with basic type.
    }
}
```

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
