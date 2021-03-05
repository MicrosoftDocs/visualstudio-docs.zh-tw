---
description: 傳回指定之標記值在父快速鍵對應存根函式中對應之變數的符號列舉。
title: IDiaSession：： findSymbolsForAcceleratorPointerTag |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 95fd5e7a-c637-437e-b369-c864eef733c2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4d1a177cd1c36a2e51f846bf60edfbef875a51df
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158926"
---
# <a name="idiasessionfindsymbolsforacceleratorpointertag"></a>IDiaSession::findSymbolsForAcceleratorPointerTag
傳回指定之標記值在父快速鍵對應存根函式中對應之變數的符號列舉。

## <a name="syntax"></a>語法

```C++
HRESULT findSymbolsForAcceleratorPointerTag ( 
   IDiaSymbol*           parent,
   DWORD                 tagValue,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>參數
 `parent`

在對應至要搜尋之快速鍵對應函式的 IDiaSymbol。

 `tagValue`

在指標標記值。

 `ppResult`

擴展以 `IDiaEnumSymbols` 結果初始化之介面指標的指標。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
