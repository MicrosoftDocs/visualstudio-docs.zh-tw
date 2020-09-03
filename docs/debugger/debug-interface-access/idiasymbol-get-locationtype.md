---
title: IDiaSymbol::get_locationType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_locationType method
ms.assetid: fbb09c43-ebb7-4b4f-be53-ccff86eb183a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 244f9c1b696b03a085e665c5e45abf200c5774cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85462970"
---
# <a name="idiasymbolget_locationtype"></a>IDiaSymbol::get_locationType
捕獲資料符號的位置類型。

## <a name="syntax"></a>語法

```C++
HRESULT get_locationType ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展傳回 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md) 列舉中的值，這個值會指定資料符號的位置類型，例如 `static` 或 `local` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)