---
title: IDiaAddressMap::set_addressMap | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 4af506da822a7f8e38a8952d7c1d0d15fc1995d2
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468550"
---
# <a name="idiaaddressmapset_addressmap"></a>IDiaAddressMap::set_addressMap
提供位址對應以支援影像版面配置翻譯。

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

在參數中的元素數目 `data` 。

 `data[]`

在定義轉譯對應之[DiaAddressMapEntry 結構](../../debugger/debug-interface-access/diaaddressmapentry.md)結構的陣列。

 `imagetoSymbols`

[in] `TRUE`如果 `data` 參數定義從新影像配置到原始版面配置的對應（如 debug 符號所述）。 `FALSE`如果 `data` 是從原始版面配置取得之新影像配置的對應。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="remarks"></a>備註
 通常，DIA 會從程式資料庫（.pdb）檔案中抓取位址轉譯對應。 如果遺漏這些值，則會呼叫[IDiaAddressMap：： set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)方法兩次，一次會將 `imagetoSymbols` 參數設定為， `TRUE` 並將 `imagetoSymbols` 參數設定為 `FALSE` 。 除非提供兩個轉譯對應，否則無法使用[IDiaAddressMap：:p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)方法來啟用位址對應翻譯。

## <a name="see-also"></a>另請參閱
- [DiaAddressMapEntry 結構](../../debugger/debug-interface-access/diaaddressmapentry.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)