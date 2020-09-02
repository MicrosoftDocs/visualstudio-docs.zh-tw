---
title: IDiaStackFrame::get_cplusplusExceptionHandling | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_cplusplusExceptionHandling method
ms.assetid: f2631820-c986-40ca-b61e-230d7a9c426c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ebc2e4042185b17d7e2f670456cf124c5ce079fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85465118"
---
# <a name="idiastackframeget_cplusplusexceptionhandling"></a>IDiaStackFrame::get_cplusplusExceptionHandling
捕獲旗標，指出 c + + 例外狀況處理是否有效。

## <a name="syntax"></a>語法

```C++
HRESULT get_cplusplusExceptionHandling ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展 `TRUE` 如果 c + + 例外狀況處理在這個框架中為作用中，則傳回，否則傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援屬性，則傳回。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 C + + 例外狀況處理與結構化或系統例外狀況處理不同。

 若要判斷結構化例外狀況處理是否有效，請呼叫 [IDiaStackFrame：： get_systemExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-systemexceptionhandling.md) 方法。

## <a name="see-also"></a>另請參閱
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackFrame::get_systemExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-systemexceptionhandling.md)