---
title: IDiaSymbol::get_unmodifiedType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_unmodifiedType method
ms.assetid: bf914dc0-ff84-4f5d-9f75-1733b17f3be0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47841f5fe4abeafe7c522784db337b1960081439
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738975"
---
# <a name="idiasymbolget_unmodifiedtype"></a>IDiaSymbol::get_unmodifiedType
抓取這個符號的原始類型。 當[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)設定為類型時，請使用。

## <a name="syntax"></a>語法

```C++
HRESULT get_unmodifiedType( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，代表這個符號的原始類型。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。

> [!NOTE]
> `S_FALSE` 的傳回值表示該屬性不適用於符號。

## <a name="remarks"></a>備註
 目前的類型是修改傳回的原始類型。 您可以先取得符號的類型，然後詢問原始類型傳回的類型，以判斷符號的原始類型。 請注意，某些符號可能不會有原始類型的修改類型。

## <a name="requirements"></a>需求
 標頭： Dia2。h

 程式庫： diaguids

 DLL： msdia100

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)