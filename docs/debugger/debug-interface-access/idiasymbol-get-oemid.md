---
title: IDiaSymbol::get_oemId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_oemId method
ms.assetid: c472830f-c3eb-46ab-9498-cd637763d241
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d417b0c75db1b2153e9a43eb2e45f3d9550971d1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739610"
---
# <a name="idiasymbolget_oemid"></a>IDiaSymbol::get_oemId
抓取符號的原始設備製造商（OEM）識別碼值。

## <a name="syntax"></a>語法

```C++
HRESULT get_oemId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回可識別 OEM 的唯一值。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。

> [!NOTE]
> @No__t_0 的傳回值表示該屬性不適用於符號。

## <a name="remarks"></a>備註
 這個屬性只適用于[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)類型為 `SymTagCustomType` 的符號。

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)