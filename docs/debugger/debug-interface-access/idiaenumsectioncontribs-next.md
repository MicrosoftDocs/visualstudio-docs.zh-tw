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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 55c4dcef489c56688321497c93448d83ce342b1b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856457"
---
# <a name="idiaenumsectioncontribsnext"></a>IDiaEnumSectionContribs::Next
抓取列舉序列中指定的區段貢獻數目。

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

擴展要填入 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) 物件的陣列，這些物件代表所需的區段貢獻。

 pceltFetched

擴展傳回取得的列舉值中的區段貢獻數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果沒有其他區段投稿，則傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)