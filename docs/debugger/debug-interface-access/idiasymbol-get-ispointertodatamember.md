---
title: IDiaSymbol::get_isPointerToDataMember |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ef17c737-242e-43e8-b7e1-2c3bc58cfcef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d74c2ba8317098212c7263ab049becc52f874e9
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "62836576"
---
# <a name="idiasymbolgetispointertodatamember"></a>IDiaSymbol::get_isPointerToDataMember
指定這個符號是否為資料成員的指標。

## <a name="syntax"></a>語法

```C++
HRESULT get_isPointerToDataMember(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>參數
 `pRetVal`

[out]指標`BOOL`，指定這個符號是否為資料成員的指標。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)