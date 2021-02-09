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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 110ce322946d1712f75ad68963299455c7865a52
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856247"
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

在要抓取之 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) 物件的索引。 索引位於0到-1 的範圍內 `count` ，其中 `count` 是 [IDiaEnumSourceFiles：： get_Count](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md) 方法所傳回的。

 sourceFile

擴展傳回代表所需來源檔案的 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)