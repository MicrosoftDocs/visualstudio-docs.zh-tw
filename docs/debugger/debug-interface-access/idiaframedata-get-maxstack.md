---
title: IDiaFrameData::get_maxStack | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_maxStack method
ms.assetid: 2585e13c-c0f3-49fe-9a84-08adb0dbeaa4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c266c5e823bd77315d184133947df225935fbcb3
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467292"
---
# <a name="idiaframedataget_maxstack"></a>IDiaFrameData::get_maxStack
抓取框架中堆疊推送的最大位元組數目。

## <a name="syntax"></a>語法

```C++
HRESULT get_maxStack ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回堆疊上推送的最大位元組數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援此屬性，則傳回。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法所傳回的值通常用於程式字串的轉譯（請參閱[IDiaFrameData：： get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)方法以取得程式字串的定義）。

## <a name="see-also"></a>另請參閱
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)