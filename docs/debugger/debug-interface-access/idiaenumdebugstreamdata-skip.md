---
title: IDiaEnumDebugStreamData：： Skip |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Skip method
ms.assetid: 106ae1d3-a379-4077-babf-2665e697b0c4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 38cfb559f79567bced9adb501f38220f33a44692
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857024"
---
# <a name="idiaenumdebugstreamdataskip"></a>IDiaEnumDebugStreamData::Skip
略過列舉序列中指定數目的記錄。

## <a name="syntax"></a>語法

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>參數
 celt

在列舉順序中要跳過的記錄數目。

## <a name="return-value"></a>傳回值
 如果成功， `S_OK` 則傳回; 否則， `S_FALSE` 如果沒有其他要略過的記錄，則會傳回。

## <a name="see-also"></a>另請參閱
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)