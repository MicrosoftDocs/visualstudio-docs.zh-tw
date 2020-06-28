---
title: IDiaSession：： findSymbolByRVAEx |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByRVAEx method
ms.assetid: 61344966-fed4-4c02-9e27-20356ec2ef7c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 807025265de5c088f1af24ec76402cdbf3a516a7
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465549"
---
# <a name="idiasessionfindsymbolbyrvaex"></a>IDiaSession::findSymbolByRVAEx
抓取指定的符號類型，其中包含或最接近指定的相對虛擬位址（RVA）和位移。

## <a name="syntax"></a>語法

```C++
HRESULT findSymbolByRVAEx ( 
   DWORD        rva,
   SymTagEnum   symtag,
   IDiaSymbol** ppSymbol,
   LONG*        displacement
);
```

#### <a name="parameters"></a>參數
 `rva`

在指定 RVA。

 `symtag`

在要尋找的符號類型。 值取自[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)列舉。

 `ppSymbol`

脫銷傳回代表所抓取符號的[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件。

 `displacement`

脫銷傳回值，指定在中指定的相對虛擬位址的位移 `rva` 。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="example"></a>範例

```C++
IDiaSymbol* pFunc;
LONG disp = 0;
pSession->findSymbolByRVAEx( rva, SymTagFunction, &pFunc, &disp );
```

## <a name="see-also"></a>另請參閱
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)