---
title: IDiaSymbol::findInlineFramesByAddr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 36a122e6-f27e-40cd-9784-cdaf279e1905
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c45e99ecab38146f6ccba9fbaf176cdf5fddb67
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464482"
---
# <a name="idiasymbolfindinlineframesbyaddr"></a>IDiaSymbol::findInlineFramesByAddr
抓取列舉型別，可讓用戶端逐一查看指定位址上的所有內嵌框架。

## <a name="syntax"></a>語法

```C++
HRESULT findInlineFramesByAddr ( 
   DWORD             isect,
   DWORD             offset,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>參數
 `isect`

在指定位址的區段元件。

 `offset`

在指定位址的位移元件。

 `ppResult`

脫銷保存 `IDiaEnumSymbols` 物件，其中包含所抓取之框架的清單。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)