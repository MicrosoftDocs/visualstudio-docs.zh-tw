---
title: IDiaEnumInjectedSources::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: bb1502c875c04955578686113d8ad491311e800d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554127"
---
# <a name="idiaenuminjectedsourcesclone"></a>IDiaEnumInjectedSources::Clone
建立列舉值，包含目前的列舉值相同的列舉型別狀態。

## <a name="syntax"></a>語法

```C++
HRESULT Clone ( 
   IDiaEnumInjectedSources** ppenum
);
```

#### <a name="parameters"></a>參數
 `ppenum`

[out]傳回[IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)物件，包含列舉值重複。 插入的來源不會重複，列舉值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)