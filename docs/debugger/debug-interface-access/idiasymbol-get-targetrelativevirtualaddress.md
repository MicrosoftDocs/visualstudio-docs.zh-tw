---
title: IDiaSymbol::get_targetRelativeVirtualAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_targetRelativeVirtualAddress method
ms.assetid: 49a159f3-6943-44d3-90a3-0dba51e8a7ec
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6648be961999e5eaf156f2c4b0dea511aed4eb59
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461848"
---
# <a name="idiasymbolget_targetrelativevirtualaddress"></a>IDiaSymbol::get_targetRelativeVirtualAddress
抓取 Thunk 目標的相對虛擬位址（RVA）。

## <a name="syntax"></a>語法

```C++
HRESULT get_targetRelativeVirtualAddress ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回 Thunk 目標的 RVA。

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