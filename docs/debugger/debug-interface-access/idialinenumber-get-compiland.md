---
title: IDiaLineNumber：： get_compiland |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_compiland method
ms.assetid: c476d0b8-c473-47eb-96f5-c4e8f577b1c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d6af27370135441ead74692c5409155ff4564b51
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466923"
---
# <a name="idialinenumberget_compiland"></a>IDiaLineNumber::get_compiland
抓取提供影像文字位元組之編譯模組符號的參考。

## <a name="syntax"></a>語法

```C++
HRESULT get_compiland ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>參數
 pRetVal

脫銷傳回提供影像文字位元組之編譯模組的[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援此屬性，則傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)