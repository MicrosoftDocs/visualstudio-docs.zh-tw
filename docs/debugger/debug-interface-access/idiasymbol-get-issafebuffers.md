---
title: IDiaSymbol：： get_isSafeBuffers |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isSafeBuffers method
ms.assetid: f29e373d-e7bb-4181-ab9f-bf708d401d83
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84123d88bc379ea670caca90d66207fc6e16f26f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85463208"
---
# <a name="idiasymbolget_issafebuffers"></a>IDiaSymbol::get_isSafeBuffers
抓取旗標，這個旗標會指定是否使用安全緩衝區的預處理器指示詞。 當 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md) 設定為時，請使用 `SymTagFunction` 。

## <a name="syntax"></a>語法

```C++
HRESULT get_isSafeBuffers( 
   BOOL* pRetVal)
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展 `TRUE` 如果指標使用安全緩衝區的預處理器指示詞，則傳回，否則傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。

## <a name="remarks"></a>備註

## <a name="requirements"></a>需求
 標頭： Dia2。h

 程式庫： diaguids .lib

 DLL： msdia100.dll

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [strict_gs_check](/cpp/preprocessor/strict-gs-check)