---
description: 抓取新增至每個函式的額外填充板大小。
title: IDiaSymbol：： get_framePadSize |Microsoft Docs
ms.date: 04/27/2021
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_framePadSize method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d361ec3e144730e49345d3560f815ee5fe0be469
ms.sourcegitcommit: 30c404655fb83ea28f96ab1edb1c09b4d8d7eec4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2021
ms.locfileid: "108217223"
---
# <a name="idiasymbolget_framepadsize"></a>IDiaSymbol：： get_framePadSize

抓取新增至每個函式的額外填充板大小。

## <a name="syntax"></a>語法

```C++
HRESULT get_framePadSize ( 
   DWORD* pPadSize
);
```

#### <a name="parameters"></a>參數

 `pPadSize`

擴展傳回已新增至每個函式的額外填充區大小。

## <a name="return-value"></a>傳回值

 如果成功， `S_OK` 則傳回; 否則傳回 `S_FALSE` 錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。

## <a name="remarks"></a>備註

[編輯後繼續] 通常會使用額外的板大小。

從 Visual Studio 2019 16.10 Preview 2 版開始支援此方法。

## <a name="requirements"></a>規格需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本：|DIA SDK v7.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
