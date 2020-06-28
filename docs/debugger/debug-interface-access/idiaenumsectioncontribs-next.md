---
title: IDiaEnumSectionContribs::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 09622b1b152a8d1efd105b9b18a3c1fa74835378
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468111"
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
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果沒有其他區段的貢獻，則傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)