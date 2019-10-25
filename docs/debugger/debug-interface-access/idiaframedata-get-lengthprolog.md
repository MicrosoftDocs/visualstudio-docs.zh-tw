---
title: IDiaFrameData::get_lengthProlog | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_lengthProlog method
ms.assetid: 5f042ff1-e74e-430a-be34-d2cf1b18eff2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00b85d1db996487d76d396d6e4df9ea557e6aae5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743553"
---
# <a name="idiaframedataget_lengthprolog"></a>IDiaFrameData::get_lengthProlog
抓取區塊中序言程式碼的位元組數目。

## <a name="syntax"></a>語法

```C++
HRESULT get_lengthProlog ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回序言碼的位元組數目。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 如果不支援此屬性，則傳回 `S_FALSE`。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 序言代碼是一系列的指令，可保留暫存器、設定 CPU 狀態，並建立函式的堆疊。

## <a name="see-also"></a>請參閱
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)