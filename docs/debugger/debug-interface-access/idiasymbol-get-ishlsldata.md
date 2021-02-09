---
title: IDiaSymbol::get_isHLSLData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4662058b-c505-4ccf-ae03-739a62c814ca
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 56f65e8160165485aab4718d13e9417bd0e92523
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863190"
---
# <a name="idiasymbolget_ishlsldata"></a>IDiaSymbol::get_isHLSLData
指定此符號是否代表高階著色器語言 (HLSL) 資料。

## <a name="syntax"></a>語法

```C++
HRESULT get_isHLSLData(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展的指標 `BOOL` ，指定此符號是否代表 HLSL 的資料。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)