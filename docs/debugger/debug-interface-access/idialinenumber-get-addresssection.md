---
title: IDiaLineNumber::get_addressSection | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_addressSection method
ms.assetid: a01c1bae-04b2-4c30-8621-60939a3124c2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56a79ea8ba7c4e5622ee468cec8fe6cb53dd197c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56615984"
---
# <a name="idialinenumbergetaddresssection"></a>IDiaLineNumber::get_addressSection
擷取區塊的開始位置的記憶體位址的區段部分。

## <a name="syntax"></a>語法

```C++
HRESULT get_addressSection ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 pRetVal

[out]傳回的記憶體位址的區段部分區塊的開始位置。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 否則會傳回錯誤碼。

## <a name="example"></a>範例

```C++
CComPtr< IDiaLineNumber > pLine;
DWORD seg;
pLine->get_addressSection( &seg );
```

## <a name="see-also"></a>請參閱
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
- [IDiaLineNumber::get_addressOffset](../../debugger/debug-interface-access/idialinenumber-get-addressoffset.md)