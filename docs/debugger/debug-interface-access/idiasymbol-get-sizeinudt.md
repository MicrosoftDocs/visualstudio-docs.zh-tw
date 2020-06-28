---
title: IDiaSymbol::get_sizeInUdt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: a82ab896-0185-46a4-b4d5-babfcc660fe1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ba2f0351997b5f6a2a96cb035871b116b9180786
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461981"
---
# <a name="idiasymbolget_sizeinudt"></a>IDiaSymbol::get_sizeInUdt
抓取使用者定義類型的成員大小。

## <a name="syntax"></a>語法

```C++
HRESULT get_sizeInUdt(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷`DWORD`的指標，指定成員的大小。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)