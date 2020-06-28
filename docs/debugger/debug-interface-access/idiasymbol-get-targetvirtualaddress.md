---
title: IDiaSymbol::get_targetVirtualAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_targetVirtualAddress method
ms.assetid: a0a5ce72-95f8-443e-bb4b-8c21194faad0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe19daf3271006e177677d490ccccd89ee293af2
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461820"
---
# <a name="idiasymbolget_targetvirtualaddress"></a>IDiaSymbol::get_targetVirtualAddress
抓取 Thunk 目標的虛擬位址（VA）。

## <a name="syntax"></a>語法

```C++
HRESULT get_targetVirtualAddress ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回 Thunk 目標的 VA。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示此屬性無法用於符號。

## <a name="remarks"></a>備註
 只有當符號做為的[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)值時，這個屬性才有效 `SymTagThunk` 。

 「Thunk」是一段程式碼，可在32位記憶體位址空間（也稱為一般位址空間）和16位位址空間（稱為分段位址空間）之間進行轉換。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)