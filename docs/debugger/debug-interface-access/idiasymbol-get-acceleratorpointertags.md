---
title: IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f36b4bf9fdd362f4941e33745d59d481a473c607
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741107"
---
# <a name="idiasymbolget_acceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
傳回對應至C++ AMP 快速鍵 stub 函數的所有快速鍵指標標記值。

## <a name="syntax"></a>語法

```C++
HRESULT get_acceleratorPointerTags(
   DWORD          cnt,
   DWORD*         pcnt,
   DWORD*         pPointerTags);
```

#### <a name="parameters"></a>參數
 `cnt`

在輸出陣列 `pPointerTags` 的大小。

 `pcnt`

脫銷C++ AMP 加速器存根函式中的快速鍵指標標記計數。

 `pPointerTags`

脫銷@No__t_0 的陣列指標，它會填入C++ AMP 加速器 stub 函式中的快速鍵指標標記值。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。

## <a name="remarks"></a>備註
 這個方法是在對應到C++ AMP 加速器 stub 函數的 `IDiaSymbol` 介面上呼叫。

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)