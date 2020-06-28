---
title: IDiaEnumSymbols：： Skip |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Skip method
ms.assetid: e601fbc9-b10b-41c7-8180-959e57efabe8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fea037e4e99cc5c8822987c30a94adf37ebe276e
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467705"
---
# <a name="idiaenumsymbolsskip"></a>IDiaEnumSymbols::Skip
略過列舉序列中指定數目的符號。

## <a name="syntax"></a>語法

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>參數
 celt

在要略過的列舉序列中的符號數目。

## <a name="return-value"></a>傳回值
 如果成功， `S_OK` 會傳回; 否則， `S_FALSE` 如果沒有其他要略過的符號，則會傳回。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)