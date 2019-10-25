---
title: IDiaEnumSectionContribs::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Next method
ms.assetid: a6bb2adb-ee6d-4f3c-ab5b-e89361c8880e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 61d99b0c881abdb8974e94352911ae3234c440c1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744267"
---
# <a name="idiaenumsectioncontribsnext"></a>IDiaEnumSectionContribs::Next
抓取列舉序列中指定數目的區段貢獻。

## <a name="syntax"></a>語法

```C++
HRESULT Next( 
   ULONG                celt,
   IDiaSectionContrib** rgelt,
   ULONG*               pceltFetched
);
```

#### <a name="parameters"></a>參數
 celt

在要抓取的列舉值中的區段貢獻數目。

 rgelt

脫銷要填入[IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)物件的陣列，表示所需的區段投稿。

 pceltFetched

脫銷傳回已提取列舉值中的區段貢獻數目。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 如果沒有其他區段的貢獻，則傳回 `S_FALSE`。 否則會傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)