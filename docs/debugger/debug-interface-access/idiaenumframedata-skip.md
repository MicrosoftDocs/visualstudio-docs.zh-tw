---
title: IDiaEnumFrameData：： Skip |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Skip method
ms.assetid: 67140b4c-7125-4895-932d-42412326da29
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c49aaf1f648a52e1701088b6579eda55cde6c355
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744576"
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

在列舉序列中要略過的框架資料元素數目。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，如果沒有其他要略過的記錄，則會傳回 `S_FALSE`。

## <a name="see-also"></a>請參閱
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)