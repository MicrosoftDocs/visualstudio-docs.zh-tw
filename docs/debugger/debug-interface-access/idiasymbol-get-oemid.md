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
ms.openlocfilehash: 8cc6cd3e7948b88169489cf4f4c73d1e8fcc7d73
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56641178"
---
# <a name="idiasymbolgetoemid"></a>IDiaSymbol::get_oemId
擷取符號的原始設備製造商 (OEM) 的識別碼值。

## <a name="syntax"></a>語法

```C++
HRESULT get_oemId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

[out]傳回唯一值，這個值可識別 OEM。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。

> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不是適用於符號。

## <a name="remarks"></a>備註
 這個屬性只適用於具有符號[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)種`SymTagCustomType`。

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)