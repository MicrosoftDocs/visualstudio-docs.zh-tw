---
title: IDiaSymbol：： findChildrenEx |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenEx
ms.assetid: 6e045045-da8c-4338-9423-81a1ca20c405
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26fdced012baada390cdd0a112856b592d3c923e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741274"
---
# <a name="idiasymbolfindchildrenex"></a>IDiaSymbol::findChildrenEx
抓取符號的子系。 如果程式是使用的優化來編譯，則傳回的區域符號會包含即時範圍資訊。

## <a name="syntax"></a>語法

```C++
HRESULT findChildrenEx ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>參數
 `symtag`

在指定要抓取之子系的符號標記（如[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)中所定義）。 針對要抓取的所有子系，設定為 `SymTagNull`。

 `name`

在指定要抓取之子系的名稱。 針對要抓取的所有子系，設定為 `NULL`。

 `compareFlags`

在指定要套用至名稱比對的比較選項。 來自[NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)列舉的值可以單獨使用，或搭配使用。

 `ppResult`

脫銷傳回[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)物件，其中包含所抓取之子符號的清單。

## <a name="return-value"></a>傳回值
 如果找到至少一個符號子系，則傳回 `S_OK`，如果找不到子系，則傳回 `S_FALSE`;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法是[IDiaSymbol：： findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)的擴充版本。

## <a name="requirements"></a>需求
 標頭： Dia2。h

 程式庫： diaguids

 DLL： msdia100

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)