---
title: IDiaSymbol：： get_isAcceleratorStubFunction |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: cc4ea375-76f6-4ba8-baed-c5fa82108137
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcc8128ec5c9693b399c08a134326b1f6d135d1b
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463488"
---
# <a name="idiasymbolget_isacceleratorstubfunction"></a>IDiaSymbol::get_isAcceleratorStubFunction
指出符號是否對應至針對對應至呼叫之快速鍵所編譯之著色器的最上層函式符號 `parallel_for_each` 。

## <a name="syntax"></a>語法

```C++
HRESULT get_isAcceleratorStubFunction(
   BOOL* pFlag);
```

#### <a name="parameters"></a>參數
 `pFlag`

脫銷的指標 `BOOL` ，指出符號是否對應至針對對應至呼叫之快速鍵所編譯之著色器的最上層函式符號 `parallel_for_each` 。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)