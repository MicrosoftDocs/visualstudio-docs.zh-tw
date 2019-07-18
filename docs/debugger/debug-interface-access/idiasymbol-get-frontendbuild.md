---
title: 'Idiasymbol:: Get_frontendbuild |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_frontEndBuild method
ms.assetid: f7dab1c6-112b-4966-baa5-afc976949c76
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8af52d36370d8778c38c2ddead446d66b5d46eba
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "64803218"
---
# <a name="idiasymbolgetfrontendbuild"></a>IDiaSymbol::get_frontEndBuild
擷取後端的組建編號。

## <a name="syntax"></a>語法

```C++
HRESULT get_frontEndBuild ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

[out]傳回前端組建編號。 請參閱＜備註＞。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。

> [!NOTE]
> 傳回值為`S_FALSE`表示屬性不是適用於符號。

## <a name="remarks"></a>備註
 編譯器通常由兩個主要項目所組成： 前端 （剖析器），以處理剖析原始程式碼以中繼形式和一個後端 （程式碼產生器），然後將中繼的形式轉換成組件。 您不可能發生的前端與後端的不同版本的狀況。

 前端或後端版本號碼是三個部分組成：\<主要 >。\<次要 >。\<建置 >，其中\<主要 > 是主要版本號碼，\<次要 > 是次要版本號碼，以及\<建置 > 是的組建編號。 例如 13.10.3077。

## <a name="requirements"></a>需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2.h|
|版本:|DIA SDK v7.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)