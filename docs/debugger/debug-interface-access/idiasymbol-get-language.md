---
title: IDiaSymbol::get_language | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_language method
ms.assetid: c759ad3c-1c21-4234-869b-86aa3a608a38
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e7dc0a0a640a9d3921801a9077b32ade5921ff7
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463117"
---
# <a name="idiasymbolget_language"></a>IDiaSymbol::get_language
抓取來源的語言。

## <a name="syntax"></a>語法

```C++
HRESULT get_language ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷從指定來來源語言的[CV_CFL_LANG 列舉](../../debugger/debug-interface-access/cv-cfl-lang.md)列舉傳回值。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示此屬性無法用於符號。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [CV_CFL_LANG 列舉](../../debugger/debug-interface-access/cv-cfl-lang.md)