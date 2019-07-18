---
title: IDiaSymbol::get_hasDebugInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasDebugInfo method
ms.assetid: 84cd2b67-0d83-4589-9ecb-a4bcbeed55f5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b7369437c684b63b1caf3f55d3cc4d852d6eac0
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "64801373"
---
# <a name="idiasymbolgethasdebuginfo"></a>IDiaSymbol::get_hasDebugInfo
擷取指定的旗標[編譯模組](../../debugger/debug-interface-access/compiland.md)包含偵錯資訊。

## <a name="syntax"></a>語法

```C++
HRESULT get_hasDebugInfo(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>參數
 `pFlag`

[out]會傳回`TRUE`編譯模組包含偵錯資訊; 否則會傳回`FALSE`。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。

> [!NOTE]
> 傳回值為`S_FALSE`表示屬性不是適用於符號。

## <a name="requirements"></a>需求

|需求|說明|
|-----------------|-----------------|
|標頭：|dia2.h|
|版本:|DIA SDK v8.0|

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)