---
description: 抓取旗標，這個旗標會指定是否封裝 (UDT) 的使用者定義資料類型。
title: IDiaSymbol：： get_packed |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_packed method
ms.assetid: e42ff368-56c4-49a2-8676-f80e349efa21
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a5e6cf89aa0bdd31b826ac8e73000c1bfa8c595c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161932"
---
# <a name="idiasymbolget_packed"></a>IDiaSymbol::get_packed
抓取旗標，這個旗標會指定是否封裝 (UDT) 的使用者定義資料類型。

## <a name="syntax"></a>語法

```C++
HRESULT get_packed ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展 `TRUE` 如果 UDT 已封裝，則傳回，否則傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該屬性不適用於符號。

## <a name="remarks"></a>備註
 封裝表示 UDT 的所有成員都盡可能地放在最接近的位置，不會有任何中間填補，以配合記憶體界限。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
