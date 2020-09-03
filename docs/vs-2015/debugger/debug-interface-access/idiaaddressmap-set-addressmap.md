---
title: IDiaAddressMap::set_addressMap | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 693ecf6e8fd4f0b55936bde371b7baa6975b8f2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198659"
---
# <a name="idiaaddressmapset_addressmap"></a>IDiaAddressMap::set_addressMap
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

提供可支援影像版面配置翻譯的位址對應。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 在定義平移對應之 [DiaAddressMapEntry 結構](../../debugger/debug-interface-access/diaaddressmapentry.md) 結構的陣列。  
  
 `imagetoSymbols`  
 [in] `TRUE` 如果 `data` 參數定義從新影像配置到原始配置 (的對應，如 debug 符號) 所述。 `FALSE` 如果 `data` 是，則是從原始版面配置取得新影像配置的對應。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 通常，DIA 會從程式資料庫 ( .pdb) 檔中取出位址轉譯。 如果遺漏這些值，則會呼叫 [IDiaAddressMap：： set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) 方法兩次，一次是 `imagetoSymbols` 將參數設定為 `TRUE` ，而將 `imagetoSymbols` 參數設定為 `FALSE` 。 除非提供這兩個轉譯對應，否則無法使用 [IDiaAddressMap：:p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) 方法來啟用位址對應轉譯。  
  
## <a name="see-also"></a>另請參閱  
 [DiaAddressMapEntry 結構](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap：:p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
