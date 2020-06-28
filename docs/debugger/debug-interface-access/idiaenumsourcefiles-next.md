---
title: IDiaEnumSourceFiles::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 7081c85d64e76900d6f310cfc8ff6cde51087fc3
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467908"
---
# <a name="idiaenumsourcefilesnext"></a>IDiaEnumSourceFiles::Next
在列舉序列中，抓取指定的來源檔案數目。

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

在列舉值中要抓取的來源檔案數目。

 rgelt

脫銷要填入的陣列，其中包含代表所需來源檔案的[IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)物件。

 pceltFetched

脫銷傳回提取枚舉器中的原始檔數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果沒有其他原始檔案，則傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)