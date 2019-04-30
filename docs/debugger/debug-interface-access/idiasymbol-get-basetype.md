---
title: IDiaSymbol::get_baseType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_baseType method
ms.assetid: 5c69a241-a8d3-48ed-8b36-27463a196572
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e1d38e39fd7687de3ff87737b49972cb389187aa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62837603"
---
# <a name="idiasymbolgetbasetype"></a>IDiaSymbol::get_baseType
擷取這個符號的基礎類型<em>。</em>

## <a name="syntax"></a>語法

```C++
HRESULT get_baseType (
    DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
`pRetVal`

[out]傳回值，以從[BasicType 列舉](../../debugger/debug-interface-access/basictype.md)指定符號的基底類型的列舉類型。

## <a name="return-value"></a>傳回值
如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。

> [!NOTE]
> 傳回值為`S_FALSE`表示屬性不是適用於符號。

## <a name="remarks"></a>備註
符號的基本類型可以先取得符號的類型，和接著詢問傳回基底型別的型別來判斷。 請注意一些符號可能不會有基底類型 — 例如，結構的名稱。

## <a name="example"></a>範例

```C++
IDiaSymbol* pType;
CComPtr<IDiaSymbol> pBaseType;
if (pType->get_type( &pBaseType ) == S_OK)
{
    BasicType btBaseType;
    if (pBaseType->get_baseType((DWORD *)&btBaseType) == S_OK)
    {
        // Do something with basic type.
    }
}
```

## <a name="requirements"></a>需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2.h|
|版本:|DIA SDK v7.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [BasicType 列舉](../../debugger/debug-interface-access/basictype.md)
- [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
