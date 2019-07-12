---
title: IDiaSymbol::get_optimizedCodeDebugInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_optimizedCodeDebugInfo method
ms.assetid: 57ef4170-37a9-46b0-8217-c1a674725113
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 27e2edec7964e2105cd411321a6e7644e7835097
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "64796439"
---
# <a name="idiasymbolgetoptimizedcodedebuginfo"></a>IDiaSymbol::get_optimizedCodeDebugInfo
擷取指出函數是否包含僅適用於最佳化程式碼的偵錯資訊的旗標。

## <a name="syntax"></a>語法

```C++
HRESULT get_optimizedCodeDebugInfo(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>參數
 `pFlag`

[out]會傳回`TRUE`最佳化函式或標籤中包含偵錯資訊; 否則會傳回`FALSE`。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。

> [!NOTE]
> 傳回值為`S_FALSE`表示此屬性不適用於符號。

## <a name="requirements"></a>需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2.h|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)