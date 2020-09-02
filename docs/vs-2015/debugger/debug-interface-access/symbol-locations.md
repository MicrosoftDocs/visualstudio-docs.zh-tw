---
title: 符號位置 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- LocationType values
- symbols [DIA SDK], locations
ms.assetid: 7c8cd8fe-169e-4161-9cff-5e9015984add
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1f9ea0c6f2eede11100a4956ef4c63b20c6fa9a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193562"
---
# <a name="symbol-locations"></a>符號位置
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

大部分的符號在影像檔案中都有一個已定義的位置。 符號的位置會以 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md) 列舉的值來指定。 符號可能會根據其位置支援其他屬性。  
  
 下表顯示最常使用的位置類型及其其他屬性。  
  
|位置類型|其他屬性|  
|-------------------|---------------------------|  
|`LocIsNull`|無|  
|`LocIsStatic`|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)<br /><br /> [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)<br /><br /> 如果已啟用相對虛擬位址， [IDiaSymbol：： get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md) () <br /><br /> 如果映射基底已設定為非零， [IDiaSymbol：： get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md) () |  
|`LocIsTLS`|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)<br /><br /> [IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|  
|`LocIsRegRel`|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)<br /><br /> [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsThisRel`|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsEnregistered`|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|  
|`LocIsBitField`|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)<br /><br /> [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)<br /><br /> [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsSlot`|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|  
|`LocIsIlRel`|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocInMetaData`|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|  
|`LocIsConstant`|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol：： get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)   
 [IDiaSymbol：： get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)   
 [IDiaSymbol：： get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)   
 [IDiaSymbol：： get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)   
 [IDiaSymbol：： get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [IDiaSymbol：： get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)   
 [IDiaSymbol：： get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)   
 [IDiaSymbol：： get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)   
 [IDiaSymbol：： get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)   
 [IDiaSymbol：： get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)   
 [IDiaSymbol：： get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)   
 [IDiaSymbol：： get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)   
 [LocationType 列舉](../../debugger/debug-interface-access/locationtype.md)   
 [符號和符號標記](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)
