---
title: IDiaStackFrame::get_systemExceptionHandling | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_systemExceptionHandling
ms.assetid: c76cf265-dea0-4159-883f-32b50bbef044
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7447b11008af87afe192abe935e8ea2c53ef7445
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464944"
---
# <a name="idiastackframeget_systemexceptionhandling"></a>IDiaStackFrame::get_systemExceptionHandling
抓取表示系統例外狀況處理是否有效的旗標。

## <a name="syntax"></a>語法

```C++
HRESULT get_systemExceptionHandling ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷`TRUE`如果系統例外狀況處理作用於此框架，則傳回，否則傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援此屬性，則傳回。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 系統例外狀況處理也稱為結構化例外狀況處理。 這與 c + + 例外狀況處理的做法並不相同。

 若要判斷 c + + 例外狀況處理是否有效，請呼叫[IDiaStackFrame：： get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-cplusplusexceptionhandling.md)方法。

## <a name="see-also"></a>另請參閱
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackFrame::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-cplusplusexceptionhandling.md)