---
title: IDiaEnumSectionContribs：： get_Count |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::get_Count interface
ms.assetid: 94f11de3-9393-4a5c-9814-2e6bdb597f70
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8e098af61a81702c55aa1d92a3b6425e6ef20ae4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856485"
---
# <a name="idiaenumsectioncontribsget_count"></a>IDiaEnumSectionContribs::get_Count
抓取區段投稿的數目。

## <a name="syntax"></a>語法

```C++
HRESULT get_Count ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展傳回區段投稿的數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)
- [IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)