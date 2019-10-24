---
title: IDiaEnumLineNumbers：： Skip |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Skip method
ms.assetid: d182c269-8c76-4d8b-8275-c6807c5ae4e1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 58b959db58688fd13c3539f720315971e774a96d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744365"
---
# <a name="idiaenumlinenumbersskip"></a>IDiaEnumLineNumbers::Skip
在列舉序列中略過指定數目的行號。

## <a name="syntax"></a>語法

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>參數
 celt

在要略過的列舉序列中的行號數目。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，如果沒有更多行號可略過，則會傳回 `S_FALSE`。

## <a name="see-also"></a>請參閱
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)