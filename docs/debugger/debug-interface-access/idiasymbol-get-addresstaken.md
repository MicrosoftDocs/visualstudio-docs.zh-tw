---
title: IDiaSymbol::get_addressTaken | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressTaken method
ms.assetid: 0d366188-f5e1-4226-b392-58c09539d097
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b62a848d70b59a1764220c806123b0edd03edf2
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464349"
---
# <a name="idiasymbolget_addresstaken"></a>IDiaSymbol::get_addressTaken
抓取表示另一個符號是否參考此符號位址的旗標。

## <a name="syntax"></a>語法

```C++
HRESULT get_addressTaken ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷`TRUE`如果另一個符號參考這個位址，則傳回，否則傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該屬性不適用於符號。

## <a name="example"></a>範例
 在下列範例中， `B` 參考 `A` 。 因此，符號 `A` 的 `get_addressTaken` 方法會傳回 `TRUE` 。

```C++
int A  = 0;
int* B = &A;
```

## <a name="requirements"></a>需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本：|DIA SDK v7.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)