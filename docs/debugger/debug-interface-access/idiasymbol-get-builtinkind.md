---
description: 抓取 HLSL 型別的內建類型。
title: IDiaSymbol：： get_builtInKind |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 953e6dba-582e-4b76-b736-898b92e5693e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d71ad1c8986bb60238e8fce6a5f3c7c201cb4954
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162218"
---
# <a name="idiasymbolget_builtinkind"></a>IDiaSymbol::get_builtInKind
抓取 HLSL 型別的內建類型。

## <a name="syntax"></a>語法

```C++
HRESULT get_buildInKind(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展的指標，其 `DWORD` 包含內建類型的 HLSL 類型。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
