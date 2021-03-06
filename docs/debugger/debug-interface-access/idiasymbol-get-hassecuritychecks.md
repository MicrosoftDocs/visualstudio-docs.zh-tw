---
description: 抓取旗標，這個旗標會指定編譯單位或函數是否以緩衝區溢位的安全性檢查進行編譯 (例如，/GS (緩衝區安全性檢查) ) 編譯器參數) 。
title: IDiaSymbol：： get_hasSecurityChecks |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSecurityChecks method
ms.assetid: 4bb51f62-8645-41a4-bc44-1451010623fd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 56f337a84081aa8c0282efcf07b70f30d98da15e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162065"
---
# <a name="idiasymbolget_hassecuritychecks"></a>IDiaSymbol::get_hasSecurityChecks
抓取旗標，這個旗標會指定編譯單位或函數是否以緩衝區溢位的安全性檢查進行編譯 (例如， [/gs (緩衝區安全性檢查) ](/cpp/build/reference/gs-buffer-security-check) 編譯器參數) 。

## <a name="syntax"></a>語法

```C++
HRESULT get_hasSecurityChecks(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>參數
 `pFlag`

擴展 `TRUE` 如果函數有任何安全性檢查，則傳回，否則傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該屬性不適用於符號。

## <a name="requirements"></a>規格需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本：|DIA SDK v8.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [/GS (緩衝區安全性檢查) ](/cpp/build/reference/gs-buffer-security-check)
