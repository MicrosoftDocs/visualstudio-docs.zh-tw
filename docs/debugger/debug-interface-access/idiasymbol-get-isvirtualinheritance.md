---
title: IDiaSymbol：： get_isVirtualInheritance |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 72906b92-dd4a-42e3-9b24-b77628fa48c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 67b35a40de94bec45ce9ea1f5b50472f234192d3
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463152"
---
# <a name="idiasymbolget_isvirtualinheritance"></a>IDiaSymbol::get_isVirtualInheritance
指定指標是否 `this` 指向具有虛擬繼承的資料成員。

## <a name="syntax"></a>語法

```C++
HRESULT get_isVirtualInheritance(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷的指標 `BOOL` ，指定 `this` 指標是否指向具有虛擬繼承的資料成員。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)