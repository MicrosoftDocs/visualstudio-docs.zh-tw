---
title: IDiaSectionContrib::get_nopad | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_nopad method
ms.assetid: f5c08603-0b3e-4e81-acf1-1b95a6a83bed
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51fb2c4ff2f27cee8fcc989139f5ae14c2641394
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62828109"
---
# <a name="idiasectioncontribgetnopad"></a>IDiaSectionContrib::get_nopad
擷取旗標，指出是否區段應該不會填補到下一個記憶體界限。

## <a name="syntax"></a>語法

```C++
HRESULT get_nopad(
   BOOL* pRetVal
};
```

#### <a name="parameters"></a>參數
 `pRetVal`

[out]會傳回`TRUE`如果區段應該不會填補到下一步 的記憶體界限; 否則會傳回`FALSE`。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 這是通常只能在較舊的檔案上出現的屬性。

## <a name="see-also"></a>另請參閱
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)