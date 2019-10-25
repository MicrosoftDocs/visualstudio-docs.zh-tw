---
title: IDiaEnumSourceFiles::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Skip method
ms.assetid: 4821e6dd-d33f-403d-857d-e3ae81e4a9e3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7aef3ea724bbb50f0342032a62e0044a1f0eb30
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744057"
---
# <a name="idiaenumsourcefilesskip"></a>IDiaEnumSourceFiles::Skip
略過列舉序列中指定的原始程式檔數目。

## <a name="syntax"></a>語法

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>參數
 celt

在列舉序列中要略過的來源檔案數目。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，如果沒有其他要略過的來源檔案，則會傳回 `S_FALSE`。

## <a name="see-also"></a>請參閱
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)