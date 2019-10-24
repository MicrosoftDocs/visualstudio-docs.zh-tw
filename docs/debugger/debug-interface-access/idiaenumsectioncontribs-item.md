---
title: IDiaEnumSectionContribs::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Item method
ms.assetid: 63a28f23-0ca0-44a7-b11b-ca0206d642a0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d021b5016bd0e0039f2bf175102dc44f04dabaab
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744300"
---
# <a name="idiaenumsectioncontribsitem"></a>IDiaEnumSectionContribs::Item
透過索引來抓取區段投稿。

## <a name="syntax"></a>語法

```C++
HRESULT Item ( 
   DWORD                index,
   IDiaSectionContrib** section
);
```

#### <a name="parameters"></a>參數
 索引

在要抓取的[IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)物件索引。 索引的範圍是0到 `count`-1，其中 `count` 是由[IDiaEnumSectionContribs：： get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)方法傳回。

 section

脫銷傳回[IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)物件，代表所需的區段比重。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaEnumSectionContribs::get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)