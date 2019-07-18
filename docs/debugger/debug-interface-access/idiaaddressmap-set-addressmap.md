---
title: IDiaAddressMap::set_addressMap | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 963ee64b639780bae60a4c2655db8b666d87c702
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554244"
---
# <a name="idiaaddressmapsetaddressmap"></a>IDiaAddressMap::set_addressMap
提供支援映像的版面配置轉譯對應的位址。

## <a name="syntax"></a>語法

```C++
HRESULT set_addressMap ( 
   DWORD                     cbData,
   struct DiaAddressMapEntry data[],
   BOOL                      imagetoSymbols
);
```

#### <a name="parameters"></a>參數
 `cbData`

[in]中的項目數`data`參數。

 `data[]`

[in]陣列[DiaAddressMapEntry 結構](../../debugger/debug-interface-access/diaaddressmapentry.md)結構會定義轉譯對應。

 `imagetoSymbols`

[in]`TRUE`如果`data`參數會定義新的映像版面配置的原始配置對應 （如偵錯符號所述）。 `FALSE` 如果`data`是取自原始配置新的映像版面配置的對應。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 通常，DIA 會將位址轉譯對應擷取程式資料庫 (.pdb) 檔案中。 如果這些值遺失，則[idiaaddressmap:: Set_imageheaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)方法呼叫兩次，一次使用`imagetoSymbols`參數設定為`TRUE`並一次使用`imagetoSymbols`參數設為`FALSE`。 無法使用啟用位址對應翻譯[idiaaddressmap:: Put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)方法，因此除非兩個轉譯對應所提供。

## <a name="see-also"></a>另請參閱
- [DiaAddressMapEntry 結構](../../debugger/debug-interface-access/diaaddressmapentry.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)