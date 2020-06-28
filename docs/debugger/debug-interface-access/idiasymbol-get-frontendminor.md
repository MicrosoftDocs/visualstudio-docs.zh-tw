---
title: IDiaSymbol：： get_frontEndMinor |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_frontEndMinor method
ms.assetid: 40792153-827c-4859-be7c-6aa16d5abab6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43c3ab40a694dd2ae8623bc3ed6654cf93b0a3ca
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463852"
---
# <a name="idiasymbolget_frontendminor"></a>IDiaSymbol::get_frontEndMinor
抓取前端次要版本號碼。

## <a name="syntax"></a>語法

```C++
HRESULT get_frontEndMinor ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回 front. end 次要版本號碼。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示此屬性無法用於符號。

## <a name="remarks"></a>備註
 編譯器通常是由兩個主要元素組成：前端（剖析器），它會將原始程式碼剖析成中繼格式，並使用後端（程式碼產生器），將中繼表單轉換成元件。 前端的版本與後端不同，並不罕見。

 前端或後端版本號碼是由三個部分組成： \<major> ... \<minor> \<build> ，其中 \<major> 是主要版本號碼， \<minor> 是次要版本號碼，而 \<build> 則是組建編號。 例如 13.10.3077。

## <a name="requirements"></a>需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本：|DIA SDK v7.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)