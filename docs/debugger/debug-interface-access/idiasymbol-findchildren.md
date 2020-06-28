---
title: IDiaSymbol：： findChildren |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildren method
ms.assetid: 5fe7573a-e48b-428d-9c17-7421b7209246
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f1fe583ba4932f4f534886ed1c9af34e900ba67
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464587"
---
# <a name="idiasymbolfindchildren"></a>IDiaSymbol::findChildren
抓取符號的子系。

## <a name="syntax"></a>語法

```C++
HRESULT findChildren ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>參數
 `symtag`

在指定要抓取之子系的符號標記（如[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)中所定義）。 `SymTagNull`針對要抓取的所有子系，將設為。

 `name`

在指定要抓取之子系的名稱。 `NULL`針對要抓取的所有子系，將設為。

 `compareFlags`

在指定套用至名稱比對的比較選項。 來自[NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)列舉的值可以單獨使用，或搭配使用。

 `ppResult`

脫銷傳回[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)物件，其中包含所抓取之子符號的清單。

## <a name="return-value"></a>傳回值
 `S_OK`如果找到至少一個符號子系，則傳回; 否則，如果找不到子系，則傳回 `S_FALSE` ; 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法等同于呼叫[IDiaSession：： findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)方法，並以這個符號作為第一個參數。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)