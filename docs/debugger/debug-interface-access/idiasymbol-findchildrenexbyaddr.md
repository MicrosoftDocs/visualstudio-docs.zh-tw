---
title: IDiaSymbol::findChildrenExByAddr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByAddr
ms.assetid: c1e7885d-2d15-4529-9ac2-32dd22efe31c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c0fcba05cb21aa3d19b79ac26ca5c70ace12e6d
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464573"
---
# <a name="idiasymbolfindchildrenexbyaddr"></a>IDiaSymbol::findChildrenExByAddr
抓取符號的子系，這個位置在指定的位址是有效的。

## <a name="syntax"></a>語法

```C++
HRESULT findChildrenExByAddr ( 
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

在符號的位址。

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