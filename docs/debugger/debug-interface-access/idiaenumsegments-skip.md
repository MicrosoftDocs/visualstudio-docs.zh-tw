---
title: IDiaEnumSegments::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Skip method
ms.assetid: ec67039f-da8c-4e70-8db7-957d7d5281e8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bfb2c23c0d2d751482bbd6e778ff236f7e4040db
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856324"
---
# <a name="idiaenumsegmentsskip"></a>IDiaEnumSegments::Skip
略過列舉序列中指定的區段數目。

## <a name="syntax"></a>語法

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>參數
 celt

在列舉順序中要跳過的區段數目。

## <a name="return-value"></a>傳回值
 如果成功， `S_OK` 則傳回; 否則， `S_FALSE` 如果沒有其他區段可略過，則會傳回。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)