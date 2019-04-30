---
title: IDiaSymbol::get_baseSymbol |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cabb5a18-bda7-47e8-9e46-5f4718579fc9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fd03eaead008c4014b10f9390610c7e103a4a6c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62837845"
---
# <a name="idiasymbolgetbasesymbol"></a>IDiaSymbol::get_baseSymbol
擷取來源的指標為基礎的符號。

## <a name="syntax"></a>語法

```C++
HRESULT get_baseSymbol(
   IDiaSymbol** pRetVal);
```

#### <a name="parameters"></a>參數
 `pRetVal`

[out]符號指標為基礎的指標。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseSymbolId](../../debugger/debug-interface-access/idiasymbol-get-basesymbolid.md)