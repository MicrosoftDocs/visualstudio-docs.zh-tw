---
title: IDiaSymbol：： get_thisAdjust |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thisAdjust method
ms.assetid: 56b9a147-e8c0-4d4b-a42a-398214dd5f86
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2475ccf14d892a7f7d1b130c63dbea458038dd41
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461798"
---
# <a name="idiasymbolget_thisadjust"></a>IDiaSymbol::get_thisAdjust
抓取方法的邏輯 `this` adjustor。

## <a name="syntax"></a>語法

```C++
HRESULT get_thisAdjust ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回方法的邏輯 `this` adjustor。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示此屬性無法用於符號。

## <a name="remarks"></a>備註
 在某些多重繼承案例中，方法本身必須藉 `this` 由將位移加入來計算 true 值 `this` 。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)