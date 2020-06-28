---
title: IDiaSymbol::findChildrenExByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByVA
ms.assetid: 29080009-36e4-4697-acd7-50f2e3e1bf1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e365c6bd29238717466d9e5e378909ab7a2bda4
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464559"
---
# <a name="idiasymbolfindchildrenexbyva"></a>IDiaSymbol::findChildrenExByVA
抓取符號的子系，這是在指定之虛擬位址的有效位置。

## <a name="syntax"></a>語法

```C++
HRESULT findChildrenExByVA ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   DWORD             address,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>參數
 `symtag`

在指定要抓取之子系的符號標記（如[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)中所定義）。 `SymTagNull`針對要抓取的所有子系，將設為。

 `name`

在指定要抓取之子系的名稱。 `NULL`針對要抓取的所有子系，將設為。

 `compareFlags`

在指定要套用至名稱比對的比較選項。 來自[NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)列舉的值可以單獨使用，或搭配使用。

 `address`

在指定虛擬位址。

 `ppResult`

脫銷傳回[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)物件，其中包含所抓取之子符號的清單。

## <a name="return-value"></a>傳回值
 `S_OK`如果找到至少一個符號子系，則傳回 `S_FALSE` ; 否則，如果找不到子系，則傳回; 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 傳回的區域符號包含即時範圍資訊。

## <a name="requirements"></a>需求
 標頭： Dia2。h

 程式庫： diaguids

 DLL： msdia100.dll

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)