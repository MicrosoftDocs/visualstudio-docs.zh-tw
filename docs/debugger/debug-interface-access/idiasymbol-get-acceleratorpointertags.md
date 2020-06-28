---
title: IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e2da182992999a582ea30f570734b366178a9521
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464405"
---
# <a name="idiasymbolget_acceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
傳回對應至 C++ AMP 快速鍵 stub 函數的所有快速鍵指標標記值。

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

脫銷C++ AMP 快速鍵 stub 函數中的快速鍵指標標記計數。

 `pPointerTags`

脫銷在 `DWORD` C++ AMP 快速鍵 stub 函式中填入快速鍵指標標記值的陣列指標。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

## <a name="remarks"></a>備註
 這個方法是在 `IDiaSymbol` 對應至 C++ AMP 快速鍵 stub 函數的介面上呼叫。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)