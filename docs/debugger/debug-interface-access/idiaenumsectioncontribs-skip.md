---
title: IDiaEnumSectionContribs::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Skip method
ms.assetid: 7471a178-5134-41b2-80a6-51ff96abe916
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c90c2148fc5a563fef8946bd39acf4603d7d09f6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833229"
---
# <a name="idiaenumsectioncontribsskip"></a>IDiaEnumSectionContribs::Skip
略過指定的數目的列舉型別序列中的區段比重。

## <a name="syntax"></a>語法

```C++
HRESULT Skip( 
   ULONG celt
);
```

#### <a name="parameters"></a>參數
 `celt`

[in]略過列舉序列中的區段貢獻數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`是否略過任何更多區段投稿內容。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)