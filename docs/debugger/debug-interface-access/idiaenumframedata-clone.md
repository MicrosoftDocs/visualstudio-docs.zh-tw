---
title: IDiaEnumFrameData：： Clone |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Clone Method
ms.assetid: 28a17300-1626-422f-a17a-3a4d3872c37c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c7325c861e8e5186faa4056edd9b282ab47e64d
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468361"
---
# <a name="idiaenumframedataclone"></a>IDiaEnumFrameData::Clone
建立枚舉器，其中包含與目前列舉值相同的列舉狀態。

## <a name="syntax"></a>語法

```C++
HRESULT Clone( 
   IDiaEnumFrameData** ppenum
);
```

#### <a name="parameters"></a>參數
 ppenum

脫銷傳回[IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)物件，其中包含重複的列舉值。 畫面格資料不會重複，只有枚舉器。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)