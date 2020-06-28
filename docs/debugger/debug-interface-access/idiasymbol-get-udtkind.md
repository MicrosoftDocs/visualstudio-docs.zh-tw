---
title: IDiaSymbol::get_udtKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_udtKind method
ms.assetid: 4002f887-aea6-4475-b302-67c57079fe0a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ef8254433fc67291b47247f376e22a5ac8f2bf0
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461634"
---
# <a name="idiasymbolget_udtkind"></a>IDiaSymbol::get_udtKind
抓取使用者定義型別（UDT）的各種。

## <a name="syntax"></a>語法

```C++
HRESULT get_udtKind ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷從指定 UDT 類型的[UdtKind 列舉](../../debugger/debug-interface-access/udtkind.md)列舉傳回值：結構、類別或等位。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示此屬性無法用於符號。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [UdtKind 列舉](../../debugger/debug-interface-access/udtkind.md)