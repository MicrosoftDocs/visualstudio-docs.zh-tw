---
title: IDiaSymbol::get_slot | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_slot method
ms.assetid: 97e405b8-483f-4da0-91e7-ca4d88251ecd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b4701e3274a45d16cf06ac9a25aa94448bc85b0c
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461974"
---
# <a name="idiasymbolget_slot"></a>IDiaSymbol::get_slot
抓取位置的插槽號碼。 當[LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)為時，請使用 `LocIsSlot` 。

## <a name="syntax"></a>語法

```C++
HRESULT get_slot ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回位置的插槽號碼。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該屬性不適用於符號。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)