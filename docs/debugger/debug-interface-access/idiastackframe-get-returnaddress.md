---
title: IDiaStackFrame::get_returnAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_returnAddress method
ms.assetid: 0df91981-919f-48ed-9c70-4121567d645b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fdfe3e4d52bbbfdd686c3a0394dfb5699058a69
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464972"
---
# <a name="idiastackframeget_returnaddress"></a>IDiaStackFrame::get_returnAddress
抓取框架的傳回位址。

## <a name="syntax"></a>語法

```C++
HRESULT get_returnAddress ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回框架的傳回位址。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援此屬性，則傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)