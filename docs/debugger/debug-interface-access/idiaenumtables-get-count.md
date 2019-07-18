---
title: IDiaEnumTables::get_Count | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::get_Count method
ms.assetid: 30fa316b-a746-4028-acae-4efcd2066f38
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e5cc51a166c5ac70c2db5358b893e52e2242d53
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829400"
---
# <a name="idiaenumtablesgetcount"></a>IDiaEnumTables::get_Count
擷取資料表的數目。

## <a name="syntax"></a>語法

```C++
HRESULT get_Count (    LONG* pRetVal
);

```

#### <a name="parameters"></a>參數
 `pRetVal`

[out]傳回資料表的數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)