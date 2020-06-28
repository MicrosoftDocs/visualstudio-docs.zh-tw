---
title: IDiaSymbol：： get_virtualBasePointerOffset |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBasePointerOffset method
ms.assetid: a4f2649c-6702-491c-90a1-d6d669258c51
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f18ac0aa983c36ec52cac22962d9639a30027c28
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461445"
---
# <a name="idiasymbolget_virtualbasepointeroffset"></a>IDiaSymbol::get_virtualBasePointerOffset
抓取虛擬基底指標的位移。

## <a name="syntax"></a>語法

```C++
HRESULT get_virtualBasePointerOffset ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回虛擬基底指標的位移。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該屬性不適用於符號。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)