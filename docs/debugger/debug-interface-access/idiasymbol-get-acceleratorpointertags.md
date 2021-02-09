---
title: IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1f45c212502a6f8cb065be536e5ecbb7e6b61d7b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854616"
---
# <a name="idiasymbolget_acceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
傳回對應至 C++ AMP 加速器存根函式的所有快速鍵指標標記值。

## <a name="syntax"></a>語法

```C++
HRESULT get_acceleratorPointerTags(
   DWORD          cnt,
   DWORD*         pcnt,
   DWORD*         pPointerTags);
```

#### <a name="parameters"></a>參數
 `cnt`

在輸出陣列的大小 `pPointerTags` 。

 `pcnt`

擴展C++ AMP 加速器存根函式中的快速鍵指標標記計數。

 `pPointerTags`

擴展在 `DWORD` C++ AMP 加速器存根函式中填入快速鍵指標標記值的陣列指標。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

## <a name="remarks"></a>備註
 在 `IDiaSymbol` 對應至 C++ AMP 加速器存根函式的介面上，會呼叫這個方法。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)