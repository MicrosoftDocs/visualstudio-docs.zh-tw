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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 93bb9e6cf42966b80bd2512a0cdc488ef91c7429
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864779"
---
# <a name="idialinenumberget_linenumberend"></a>IDiaLineNumber::get_lineNumberEnd
抓取語句或運算式結束時，以一為基礎的來源行號。

## <a name="syntax"></a>語法

```C++
HRESULT get_lineNumberEnd ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展傳回語句或運算式結束的行號。 如果值為零，則不會顯示結尾資訊。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援這個屬性，則傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)