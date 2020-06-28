---
title: IDiaLineNumber::get_lineNumberEnd | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_lineNumberEnd method
ms.assetid: b101853e-2bcf-47c1-acef-e13984c7ea9d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aaf1a2144831c9c0a34ebfe27cb5082887454890
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466872"
---
# <a name="idialinenumberget_linenumberend"></a>IDiaLineNumber::get_lineNumberEnd
抓取語句或運算式結束的以一為基底的原始程式列號。

## <a name="syntax"></a>語法

```C++
HRESULT get_lineNumberEnd ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回語句或運算式結束的行號。 如果值為零，則不會出現結尾資訊。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援此屬性，則傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)