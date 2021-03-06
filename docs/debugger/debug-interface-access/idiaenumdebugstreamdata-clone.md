---
description: 建立列舉值，其中包含與目前的 debug data stream 列舉值相同的列舉序列。
title: IDiaEnumDebugStreamData：： Clone |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Clone method
ms.assetid: e7f17750-0694-4634-bf34-c821cd265c2f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 59b6d603f86a09f6f00922490c094ccb3d996ef1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158215"
---
# <a name="idiaenumdebugstreamdataclone"></a>IDiaEnumDebugStreamData::Clone
建立包含與目前列舉值相同列舉順序的列舉值。

## <a name="syntax"></a>語法

```C++
HRESULT Clone ( 
   IDiaEnumDebugStreamData** ppenum
);
```

#### <a name="parameters"></a>參數
 ppenum

擴展傳回 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) 物件，其中包含重複的 debug 資料流程記錄序列。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
