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
ms.openlocfilehash: c1724ee3e81ac00ed048f323105842361ec22bc7
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56607950"
---
# <a name="idiasymbolgetacceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
傳回所有加速器指標的標記值對應至 c + + AMP 加速器虛設常式函式。

## <a name="syntax"></a>語法

```C++
HRESULT get_acceleratorPointerTags(
   DWORD          cnt,
   DWORD*         pcnt,
   DWORD*         pPointerTags);
```

#### <a name="parameters"></a>參數
 `cnt`

[in]輸出陣列的大小`pPointerTags`。

 `pcnt`

[out]在 c + + AMP 加速器虛設常式的函式中的加速器指標標記計數。

 `pPointerTags`

[out]A`DWORD`加速器指標標記值，在 c + + AMP 加速器虛設常式的函式中會填入的陣列指標。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。

## <a name="remarks"></a>備註
 在呼叫這個方法`IDiaSymbol`對應至 c + + AMP 加速器虛設常式函式的介面。

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)