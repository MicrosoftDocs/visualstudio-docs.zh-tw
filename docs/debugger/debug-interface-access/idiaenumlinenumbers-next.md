---
title: IDiaEnumLineNumbers：： Next |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Next method
ms.assetid: 363d5b40-1316-4ab8-836f-63637f619e0a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d65791fddfd09aa90a65320b4663b17ea4e8260f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856590"
---
# <a name="idiaenumlinenumbersnext"></a>IDiaEnumLineNumbers::Next
捕獲列舉序列中指定的行號數目。

## <a name="syntax"></a>語法

```C++
HRESULT Next ( 
   ULONG            celt,
   IDiaLineNumber** rgelt,
   ULONG*           pceltFetched
);
```

#### <a name="parameters"></a>參數
 celt

在要抓取的列舉值中的行號數目。

 rgelt

擴展傳回 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) 物件的陣列，這些物件代表所需的行號。

 pceltFetched

擴展傳回已提取列舉值中的行號數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果沒有其他行號，則會傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)