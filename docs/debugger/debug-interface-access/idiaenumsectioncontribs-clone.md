---
title: IDiaEnumSectionContribs：： Clone |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Clone method
ms.assetid: 81d3f3a7-3684-4e5c-b028-29b268684a2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c2e568b36d8c0ae561565f86f411a235d4fbf2b
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468179"
---
# <a name="idiaenumsectioncontribsclone"></a>IDiaEnumSectionContribs::Clone
建立枚舉器，其中包含與目前列舉值相同的列舉狀態。

## <a name="syntax"></a>語法

```C++
HRESULT Clone( 
   IDiaEnumSectionContrib** ppenum
);
```

#### <a name="parameters"></a>參數
 ppenum

脫銷傳回[IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)物件，其中包含重複的列舉值。 投稿區段不會重複，只有枚舉器。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)