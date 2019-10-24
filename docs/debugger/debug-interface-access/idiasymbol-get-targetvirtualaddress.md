---
title: IDiaSymbol::get_targetVirtualAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_targetVirtualAddress method
ms.assetid: a0a5ce72-95f8-443e-bb4b-8c21194faad0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 838d0a16224ff6732e80b67593970dfa75807fe0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739170"
---
# <a name="idiasymbolget_targetvirtualaddress"></a>IDiaSymbol::get_targetVirtualAddress
抓取 Thunk 目標的虛擬位址（VA）。

## <a name="syntax"></a>語法

```C++
HRESULT get_targetVirtualAddress ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回 Thunk 目標的 VA。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。

> [!NOTE]
> @No__t_0 的傳回值表示該屬性不適用於符號。

## <a name="remarks"></a>備註
 只有當符號做為 `SymTagThunk` 的[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)值時，這個屬性才有效。

 「Thunk」是一段程式碼，可在32位記憶體位址空間（也稱為一般位址空間）和16位位址空間（稱為分段位址空間）之間進行轉換。

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)