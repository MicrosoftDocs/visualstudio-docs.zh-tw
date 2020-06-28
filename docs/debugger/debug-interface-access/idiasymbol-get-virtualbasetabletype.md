---
title: IDiaSymbol::get_virtualBaseTableType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 858f149abb0bec444c43ea706e638def4ff930ce
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461438"
---
# <a name="idiasymbolget_virtualbasetabletype"></a>IDiaSymbol::get_virtualBaseTableType
抓取虛擬基底資料表指標的類型。

## <a name="syntax"></a>語法

```C++
HRESULT get_virtualBaseTableType(
   IDiaSymbol *pRetVal
};
```

#### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|`pRetVal`|脫銷傳回指定基表類型的[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件。|

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示此屬性無法用於符號。

## <a name="remarks"></a>備註
 虛擬基表指標（ `vbtptr` ）是 vtable 中的隱藏指標 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] ，可處理來自虛擬基類的繼承。 `vbtptr`根據繼承的類別，可以有不同的大小。

 這個方法會傳回可用來判斷 vbtptr 大小的[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件。

## <a name="requirements"></a>需求

|需求|說明|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本：|DIA SDK v8.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)