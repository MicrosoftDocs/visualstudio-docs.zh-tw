---
description: 抓取指定的符號類型，其中包含或最接近指定的位址。
title: IDiaSession::findSymbolByAddr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByAddr method
ms.assetid: c130abc5-4d0a-4d2d-8286-94fde36ddd4a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 42108d680f7303e9868065f15d320826baae7fdb
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147706"
---
# <a name="idiasessionfindsymbolbyaddr"></a>IDiaSession::findSymbolByAddr
抓取指定的符號類型，其中包含或最接近指定的位址。

## <a name="syntax"></a>語法

```C++
HRESULT findSymbolByAddr ( 
   DWORD        isect,
   DWORD        offset,
   SymTagEnum   symtag,
   IDiaSymbol** ppSymbol
);
```

#### <a name="parameters"></a>參數
 `isect`

在指定位址的區段元件。

 `offset`

在指定位址的位移元件。

 `symtag`

在要尋找的符號類型。 值取自 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md) 列舉。

 `ppSymbol`

擴展傳回代表已抓取符號的 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="example"></a>範例

```C++
IDiaSymbol* pFunc;
pSession->findSymbolByAddr( isect, offset, SymTagFunction, &pFunc );
```

## <a name="see-also"></a>另請參閱
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)
