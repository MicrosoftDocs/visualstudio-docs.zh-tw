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
ms.openlocfilehash: edbd1d8ae66e58611ab538cf0bfe695cb22b3412
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63400874"
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

|參數|描述|
|---------------|-----------------|
|`pRetVal`|[out]傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)指定類型的基底資料表的物件。|

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。

> [!NOTE]
> 傳回值為`S_FALSE`表示此屬性不適用於符號。

## <a name="remarks"></a>備註
 虛擬基底資料表的指標 (`vbtptr`) 中的隱藏指標[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]vtable 處理從虛擬基底類別繼承。 A`vbtptr`可以有不同的大小取決於繼承的類別。

 這個方法會傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)可用來判斷 vbtptr 大小的物件。

## <a name="requirements"></a>需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2.h|
|版本:|DIA SDK v8.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)