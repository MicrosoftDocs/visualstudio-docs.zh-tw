---
title: IDiaSymbol：： get_builtInKind |Microsoft Docs
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
ms.openlocfilehash: e7bc90c83ec789920d89bb424e6c7a6464c0ce8f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863533"
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