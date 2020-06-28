---
title: IDiaFrameData::get_lengthParams | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_lengthParams method
ms.assetid: a9177ed6-9ba8-4384-b411-24cad07d031b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 115f5395ff25020da1829ee74552b799682f304e
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467313"
---
# <a name="idiaframedataget_lengthparams"></a>IDiaFrameData::get_lengthParams
抓取堆疊上推送之參數的位元組數目。

## <a name="syntax"></a>語法

```C++
HRESULT get_lengthParams ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回參數的位元組數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援此屬性，則傳回。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法所傳回的值通常用於程式字串的轉譯（請參閱[IDiaFrameData：： get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)方法以取得程式字串的定義）。

## <a name="see-also"></a>另請參閱
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)