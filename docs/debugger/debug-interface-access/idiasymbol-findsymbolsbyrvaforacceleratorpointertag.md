---
title: IDiaSymbol：： findSymbolsByRVAForAcceleratorPointerTag |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de63223afda4ce5d00358fe3c06cabe90f2689aa
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464433"
---
# <a name="idiasymbolfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
假設有對應的標記值，這個方法會傳回在指定的相對虛擬位址上，此存根函式中所包含的符號列舉。

## <a name="syntax"></a>語法

```C++
HRESULT findSymbolsByRVAForAcceleratorPointerTag (
   DWORD             tagValue,
   DWORD             rva,
   IDiaEnumSymbols** ppResult);
```

#### <a name="parameters"></a>參數
 `tagValue`

在找到 pointee 符號記錄的指標標記值。

 `rva`

在Rva，用來篩選對應至具有指定標記值之 pointee 變數的符號。

 `ppResult`

脫銷介面指標的指標， `IDiaEnumSymbols` 它會以結果初始化。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

## <a name="remarks"></a>備註
 只在 `IDiaSymbol` 對應至快速鍵 stub 函式的介面上呼叫這個方法。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)