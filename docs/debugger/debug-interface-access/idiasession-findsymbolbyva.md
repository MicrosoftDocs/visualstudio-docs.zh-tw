---
title: IDiaSession::findSymbolByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByVA method
ms.assetid: 0350df23-9a5d-4e8d-8c26-7f571d8fb1af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99486de93b580a106c05a2bed862ae282f831aca
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465542"
---
# <a name="idiasessionfindsymbolbyva"></a>IDiaSession::findSymbolByVA
抓取指定的符號類型，其中包含或最接近指定的虛擬位址。

## <a name="syntax"></a>語法

```C++
HRESULT findSymbolByVA ( 
   ULONGLONG    va,
   SymTagEnum   symtag,
   IDiaSymbol** ppSymbol
);
```

#### <a name="parameters"></a>參數
 `va`

在指定虛擬位址。

 `symtag`

在要尋找的符號類型。 值取自[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)列舉。

 `ppSymbol`

脫銷傳回代表所抓取符號的[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="example"></a>範例

```C++
IDiaSymbol* pFunc;
pSession->findSymbolByVA( va, SymTagFunction, &pFunc );
```

## <a name="see-also"></a>另請參閱
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)