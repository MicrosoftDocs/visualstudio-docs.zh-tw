---
title: IDiaEnumSourceFiles::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Next method
ms.assetid: 83bf6317-ff39-4c5c-8987-cba34e7a6983
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29424c2b12884cae7f803a46e15f7183d9690d96
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829624"
---
# <a name="idiaenumsourcefilesnext"></a>IDiaEnumSourceFiles::Next
擷取列舉序列中的原始程式檔中指定的數目。

## <a name="syntax"></a>語法

```C++
HRESULT Next ( 
   ULONG            celt,
   IDiaSourceFile** rgelt,
   ULONG*           pceltFetched
);
```

#### <a name="parameters"></a>參數
 celt

[in]要擷取列舉值中的來源檔案的數目。

 rgelt

[out]陣列，其中是要在以填滿[IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)代表所需的原始程式檔的物件。

 pceltFetched

[out]擷取列舉值中傳回原始程式檔的數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 傳回`S_FALSE`如果不有任何更多的原始程式檔。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)