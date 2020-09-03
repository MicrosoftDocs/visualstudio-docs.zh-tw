---
title: IDiaSymbol::get_isReturnValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 37aaf48a-65cb-4ec2-823e-1c637a9f939c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a9a2a705250ccabe59e881bc72889596e4607f80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85463222"
---
# <a name="idiasymbolget_isreturnvalue"></a>IDiaSymbol::get_isReturnValue
指定變數是否攜帶傳回值。

## <a name="syntax"></a>語法

```C++
HRESULT get_isReturnValue(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展的指標 `BOOL` ，指定變數是否攜帶傳回值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)