---
title: IDiaSectionContrib::get_compilandId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_compilandId method
ms.assetid: 71ef2e63-d095-42b6-88d8-626e3129f0d9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e4a548a5d6e564c2be3148d63ee28913fb1143d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839520"
---
# <a name="idiasectioncontribgetcompilandid"></a>IDiaSectionContrib::get_compilandId
擷取一節的編譯模組識別項。

## <a name="syntax"></a>語法

```C++
HRESULT get_compilandId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

[out]傳回之區段的編譯模組識別碼。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)