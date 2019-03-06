---
title: IDiaSymbol::get_addressTaken | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 7c5ad583a29d38a61db6c485ad5adb3d33a4554f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56615555"
---
# <a name="idiasymbolgetaddresstaken"></a>IDiaSymbol::get_addressTaken
擷取指出另一個符號是否參考此符號的地址的旗標。

## <a name="syntax"></a>語法

```C++
HRESULT get_addressTaken ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

[out]會傳回`TRUE`另一個的符號參考這個位址; 否則會傳回`FALSE`。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。

> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不是適用於符號。

## <a name="example"></a>範例
 在下列範例中，`B`參考`A`。 因此，符號`A`的`get_addressTaken`方法會傳回`TRUE`。

```C++
int A  = 0;
int* B = &A;
```

## <a name="requirements"></a>需求

|需求|說明|
|-----------------|-----------------|
|標頭：|dia2.h|
|版本:|DIA SDK v7.0|

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)