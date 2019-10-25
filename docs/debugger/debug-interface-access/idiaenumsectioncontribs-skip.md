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
ms.openlocfilehash: cb371d841c10b64895400f66bf73159f27d68ec1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744257"
---
# <a name="idiaenumsectioncontribsskip"></a>IDiaEnumSectionContribs::Skip
略過列舉序列中指定數目的區段貢獻。

## <a name="syntax"></a>語法

```C++
HRESULT Skip( 
   ULONG celt
);
```

#### <a name="parameters"></a>參數
 `celt`

在要略過的列舉序列中的區段貢獻數目。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，如果沒有其他要略過的區段貢獻，則會傳回 `S_FALSE`。

## <a name="see-also"></a>請參閱
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)