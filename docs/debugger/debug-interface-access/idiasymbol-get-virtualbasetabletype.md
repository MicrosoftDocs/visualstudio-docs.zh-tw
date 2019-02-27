---
title: IDiaSymbol::get_virtualBaseTableType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBaseTableType method
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3be75efa175e281378e722e3d10a36cf4b612f7e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56636693"
---
# <a name="idiasymbolgetvirtualbasetabletype"></a>IDiaSymbol::get_virtualBaseTableType
擷取虛擬基底資料表的指標類型。

## <a name="syntax"></a>語法

```C++
HRESULT get_virtualBaseTableType(
   IDiaSymbol *pRetVal
};
```

#### <a name="parameters"></a>參數

|參數|說明|
|---------------|-----------------|
|`pRetVal`|[out]傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)指定類型的基底資料表的物件。|

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。

> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於符號。

## <a name="remarks"></a>備註
 虛擬基底資料表的指標 (`vbtptr`) 中的隱藏指標[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]vtable 處理從虛擬基底類別繼承。 A`vbtptr`可以有不同的大小取決於繼承的類別。

 這個方法會傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)可用來判斷 vbtptr 大小的物件。

## <a name="requirements"></a>需求

|需求|說明|
|-----------------|-----------------|
|標頭：|dia2.h|
|版本:|DIA SDK v8.0|

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)