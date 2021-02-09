---
title: IDiaEnumSectionContribs::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Skip method
ms.assetid: 7471a178-5134-41b2-80a6-51ff96abe916
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9ef9bde1498f555a14736d95a6aa9e4695f36324
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856443"
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

在列舉順序中要跳過的區段貢獻數目。

## <a name="return-value"></a>傳回值
 如果成功， `S_OK` 則傳回; 否則， `S_FALSE` 如果沒有其他區段參與可略過，則會傳回。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)