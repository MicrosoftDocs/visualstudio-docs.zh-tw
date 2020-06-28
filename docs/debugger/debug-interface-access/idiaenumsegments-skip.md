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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a17d8be6292a67475ae259e519749ba2422894a0
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467950"
---
# <a name="idiaenumsegmentsskip"></a>IDiaEnumSegments::Skip
略過列舉序列中指定數目的區段。

## <a name="syntax"></a>語法

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>參數
 celt

在列舉序列中要略過的區段數目。

## <a name="return-value"></a>傳回值
 如果成功， `S_OK` 會傳回; 否則， `S_FALSE` 如果沒有其他要略過的區段，則會傳回。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)