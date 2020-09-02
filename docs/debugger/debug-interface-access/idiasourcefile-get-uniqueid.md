---
title: IDiaSourceFile::get_uniqueId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_uniqueId method
ms.assetid: e0b8dbc0-6061-4f31-bead-2cd72be44e41
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b3f159211854e5b408d34c253a77893caf763bf2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85465196"
---
# <a name="idiasourcefileget_uniqueid"></a>IDiaSourceFile::get_uniqueId
抓取此映射的唯一唯一整數值。

## <a name="syntax"></a>語法

```C++
HRESULT get_uniqueId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展傳回這個影像的唯一唯一整數值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 比較索引鍵而非字串可加速行號處理。

## <a name="see-also"></a>另請參閱
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)