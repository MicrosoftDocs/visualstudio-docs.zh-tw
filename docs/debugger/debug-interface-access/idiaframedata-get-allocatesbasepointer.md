---
description: IDiaFrameData：： get_allocatesBasePointer 會抓取旗標，這個旗標會指出基底指標是否配置給此位址範圍內的程式碼。
title: IDiaFrameData::get_allocatesBasePointer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_allocatesBasePointer method
ms.assetid: 8a33db5d-008c-4fe5-b64f-210c9b77f686
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8fce5e5dbd12be7bae6ba1937b30c8a5d62de3ec
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157745"
---
# <a name="idiaframedataget_allocatesbasepointer"></a>IDiaFrameData::get_allocatesBasePointer
抓取旗標，這個旗標會指出基底指標是否配置給此位址範圍內的程式碼。 此方法已被取代。

## <a name="syntax"></a>語法

```C++
HRESULT get_allocatesBasePointer ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展 `TRUE` 如果已配置基底指標，則傳回，否則傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援這個屬性，則傳回。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 只有先前存取 FPO_DATA 的程式碼，或 [IDiaFrameData：： get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) 方法所傳回的程式字串為時，才應該使用此屬性 `NULL` 。 否則，程式字串包含計算先前登錄值所需的所有資訊。

## <a name="see-also"></a>另請參閱
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)
