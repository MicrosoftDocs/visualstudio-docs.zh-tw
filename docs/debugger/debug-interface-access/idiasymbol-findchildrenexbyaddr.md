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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464573"
---
# <a name="idiasymbolfindchildrenexbyaddr"></a>IDiaSymbol::findChildrenExByAddr
抓取符號的子系，此符號在指定的位址有效。

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

在指定要抓取之子系的符號標記，如 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)中所定義。 `SymTagNull`針對要取出的所有子系，設定為。

 `name`

在指定要抓取之子系的名稱。 `NULL`針對要取出的所有子系，設定為。

 `compareFlags`

在指定要套用至名稱比對的比較選項。 [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)列舉中的值可以單獨使用或合併使用。

 `address`

在符號的位址。

 `ppResult`

擴展傳回 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) 物件，其中包含已抓取之子符號的清單。

## <a name="return-value"></a>傳回值
 `S_OK`如果找不到符號的至少一個子系，則傳回，否則會傳回，否則會傳回 `S_FALSE` 錯誤碼。

## <a name="remarks"></a>備註
 傳回的本機符號包括即時範圍資訊。

## <a name="requirements"></a>需求
 標頭： Dia2。h

 程式庫： diaguids .lib

 DLL： msdia100.dll

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)