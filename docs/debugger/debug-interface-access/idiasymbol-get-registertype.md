---
title: IDiaSymbol::get_registerType |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f1c98ab0-8aef-4a07-a686-28b8a54418ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f714e5637776d6a0606246d339d3f9d2ccd9f19a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628074"
---
# <a name="idiasymbolgetregistertype"></a>IDiaSymbol::get_registerType
擷取註冊型別。

## <a name="syntax"></a>語法

```C++
HRESULT get_registerType(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>參數
 `pRetVal`

[out]指標`DWORD`保存暫存器型別。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)