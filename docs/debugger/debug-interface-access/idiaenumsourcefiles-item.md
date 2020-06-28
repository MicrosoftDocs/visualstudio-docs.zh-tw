---
title: IDiaEnumSourceFiles::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Item method
ms.assetid: 3c19d7ed-0232-4b0e-9b10-f33ed9e0c93b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5175d38da97a0b3e64ad94692c62425ba6e9cc83
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467915"
---
# <a name="idiaenumsourcefilesitem"></a>IDiaEnumSourceFiles::Item
藉由索引來抓取原始程式檔。

## <a name="syntax"></a>語法

```C++
HRESULT Item ( 
   DWORD            index,
   IDiaSourceFile** sourceFile
);
```

#### <a name="parameters"></a>參數
 索引

在要抓取的[IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)物件索引。 索引的範圍是0到 `count` -1，其中 `count` 是由[IDiaEnumSourceFiles：： get_Count](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md)方法所傳回。

 sourceFile

脫銷傳回[IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)物件，代表所需的原始程式檔。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)