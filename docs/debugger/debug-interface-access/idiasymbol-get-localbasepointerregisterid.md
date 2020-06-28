---
title: IDiaSymbol::get_localBasePointerRegisterId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_localBasePointerRegisterId method
ms.assetid: 9cbcaf00-9ace-45e1-b164-7a9439e08083
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fee917c4d275ec0f76cd3442d1ae56887667ca6c
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85462984"
---
# <a name="idiasymbolget_localbasepointerregisterid"></a>IDiaSymbol::get_localBasePointerRegisterId
抓取暫存器的識別碼，該暫存器會保存堆疊上本機變數的基底指標。 當[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)設定為時，請使用 `SymTagFunction` 。

## <a name="syntax"></a>語法

```C++
HRESULT get_localBasePointerRegisterId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回暫存器的識別碼，這個暫存器會保存堆疊上本機變數的基底指標。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示此屬性無法用於符號。

## <a name="remarks"></a>備註

## <a name="requirements"></a>需求
 標頭： Dia2。h

 程式庫： diaguids

 DLL： msdia100.dll

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)