---
description: 抓取不同的使用者定義型別 (UDT) 。
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6c49fc5b27a9af2a986b0cde1dc41b3a07df7150
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155576"
---
# <a name="idiasymbolget_udtkind"></a>IDiaSymbol::get_udtKind
抓取不同的使用者定義型別 (UDT) 。

## <a name="syntax"></a>語法

```C++
HRESULT get_udtKind ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展傳回 [UdtKind 列舉](../../debugger/debug-interface-access/udtkind.md) 列舉中的值，這個列舉型別會指定 UDT 的種類： structure、class 或 union。

## <a name="return-value"></a>傳回值
 如果成功， `S_OK` 則傳回; 否則傳回 `S_FALSE` 錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [UdtKind 列舉](../../debugger/debug-interface-access/udtkind.md)
