---
title: IDiaEnumSourceFiles::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 352c9516180c0ee0021fca4e0913f154f3b8d46f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744086"
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

在要抓取的[IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)物件索引。 索引的範圍是0到 `count`-1，其中 `count` 是由[IDiaEnumSourceFiles：： get_Count](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md)方法傳回。

 sourceFile

脫銷傳回[IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)物件，代表所需的原始程式檔。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)