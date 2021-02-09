---
title: IDiaEnumFrameData：： Skip |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Skip method
ms.assetid: 67140b4c-7125-4895-932d-42412326da29
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 52fe677fcbd349933ac827bc564fb57104918a1a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856765"
---
# <a name="idiaenumframedataskip"></a>IDiaEnumFrameData::Skip
略過列舉序列中指定數目的框架資料元素。

## <a name="syntax"></a>語法

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>參數
 celt

在列舉順序中要跳過的框架資料元素數目。

## <a name="return-value"></a>傳回值
 如果成功， `S_OK` 則傳回; 否則， `S_FALSE` 如果沒有其他要略過的記錄，則會傳回。

## <a name="see-also"></a>另請參閱
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)