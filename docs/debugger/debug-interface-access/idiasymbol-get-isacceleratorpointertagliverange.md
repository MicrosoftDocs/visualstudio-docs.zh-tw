---
title: IDiaSymbol::get_isAcceleratorPointerTagLiveRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: d195aec4-6d3c-42e0-88a5-3d463539f0b8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5a0e2d22da73402c7eb68e2a84cfe98e59fc0832
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863253"
---
# <a name="idiasymbolget_isacceleratorpointertagliverange"></a>IDiaSymbol::get_isAcceleratorPointerTagLiveRange
抓取旗標，這個旗標會指出符號是否對應到針對 C++ AMP 加速器編譯之程式碼中指標變數標記元件的 *定義範圍符號* 。 定義範圍符號是位址範圍的變數位置。

## <a name="syntax"></a>語法

```C++
HRESULT get_isAcceleratorPointerTagLiveRange(
   BOOL* pFlag);
```

#### <a name="parameters"></a>參數
 `pFlag`

擴展的指標 `BOOL` ，指出符號是否對應于定義範圍符號。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)