---
title: IDiaEnumInjectedSources::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Clone method
ms.assetid: 18038691-c140-426a-8617-27f0360650f3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a9a16b1c42bc7eedd04636a9b7bbdd6f9216463e
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468291"
---
# <a name="idiaenuminjectedsourcesclone"></a>IDiaEnumInjectedSources::Clone
建立枚舉器，其中包含與目前列舉值相同的列舉狀態。

## <a name="syntax"></a>語法

```C++
HRESULT Clone ( 
   IDiaEnumInjectedSources** ppenum
);
```

#### <a name="parameters"></a>參數
 `ppenum`

脫銷傳回[IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)物件，其中包含重複的列舉值。 插入的來源不會重複，只有枚舉器。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)