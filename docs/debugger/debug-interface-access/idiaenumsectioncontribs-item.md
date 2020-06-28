---
title: IDiaEnumSectionContribs::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 2f66d2ca43cba50d40bc7c8fc09b85bf252d352f
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468145"
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

在要抓取的[IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)物件索引。 索引的範圍是0到 `count` -1，其中 `count` 是由[IDiaEnumSectionContribs：： get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)方法所傳回。

 section

脫銷傳回[IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)物件，代表所需的區段比重。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSectionContribs::get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)