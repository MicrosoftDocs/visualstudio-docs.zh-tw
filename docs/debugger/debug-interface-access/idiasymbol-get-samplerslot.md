---
title: IDiaSymbol::get_samplerSlot | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 41c751ba-81be-4bd3-838f-8373fc146157
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe41982faadeec8ac44a0f178045b3c4dfa69b24
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56635276"
---
# <a name="idiasymbolgetsamplerslot"></a>IDiaSymbol::get_samplerSlot
擷取取樣器的位置。

## <a name="syntax"></a>語法

```C++
HRESULT get_samplerSlot(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>參數
 `pRetVal`

[out]指標`DWORD`保存的取樣器的位置。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)