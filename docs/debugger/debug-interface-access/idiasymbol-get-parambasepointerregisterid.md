---
description: 抓取保存參數基底指標的暫存器識別碼。
title: IDiaSymbol::get_paramBasePointerRegisterId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_paramBasePointerRegisterId method
ms.assetid: 9f5caeb4-5c88-4054-bf8b-50d34bbbf8c5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 25430f835ffedce3fa890c189cabc358f160a4ba
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155856"
---
# <a name="idiasymbolget_parambasepointerregisterid"></a>IDiaSymbol::get_paramBasePointerRegisterId
抓取保存參數基底指標的暫存器識別碼。 當 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md) 設定為時，請使用 `SymTagFunction` 。

## <a name="syntax"></a>語法

```C++
HRESULT get_paramBasePointerRegisterId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展傳回保存參數基底指標的暫存器識別碼。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。

## <a name="remarks"></a>備註

## <a name="requirements"></a>需求
 標頭： Dia2。h

 程式庫： diaguids .lib

 DLL： msdia100.dll

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
