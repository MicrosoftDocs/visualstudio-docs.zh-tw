---
title: IDiaSymbol::get_dataKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_dataKind method
ms.assetid: 45005ad0-8b29-4cde-9d33-6bef72f6e463
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dbeff220bdb0f3c97b8e6588ff42c31b31b97ceb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85463943"
---
# <a name="idiasymbolget_datakind"></a>IDiaSymbol::get_dataKind
捕獲資料符號的變數分類。

## <a name="syntax"></a>語法

```C++
HRESULT get_dataKind ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展從指定資料類型（例如全域、靜態或常數）的 [DataKind 列舉](../../debugger/debug-interface-access/datakind.md) 列舉中傳回值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該屬性不適用於符號。

## <a name="requirements"></a>需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本：|DIA SDK v7.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [DataKind 列舉](../../debugger/debug-interface-access/datakind.md)