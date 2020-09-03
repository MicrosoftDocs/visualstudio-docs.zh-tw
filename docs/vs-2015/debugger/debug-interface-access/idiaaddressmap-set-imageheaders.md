---
title: IDiaAddressMap：： set_imageHeaders |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 18fa69929f78d5ae661169a09db97697d98f4d94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198646"
---
# <a name="idiaaddressmapset_imageheaders"></a>IDiaAddressMap::set_imageHeaders
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

設定影像標頭，以啟用相對虛擬位址轉譯。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT set_imageHeaders (   
   DWORD cbData,  
   BYTE  data[],  
   BOOL  originalHeaders  
);  
```  
  
#### <a name="parameters"></a>參數  
 cbData  
 在標頭資料的位元組數目。 必須是 `n*sizeof(IMAGE_SECTION_HEADER)` `n` 可執行檔中區段標頭數目的位置。  
  
 data[]  
 在  `IMAGE_SECTION_HEADER` 要當做影像標頭使用的結構陣列。  
  
 originalHeaders  
 在如果 `FALSE` 映射標頭來自新映射，請將其設定為，如果映射標頭在 `TRUE` 升級前反映原始映射。 一般來說，這會設定為 `TRUE` 只與 [IDiaAddressMap：： set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) 方法的呼叫組合。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 `IMAGE_SECTION_HEADER`結構是在 Winnt 中宣告，並且代表可執行檔的影像區段標頭格式。  
  
 相對虛擬位址計算取決於 `IMAGE_SECTION_HEADER` 值。 通常，DIA 會從程式資料庫 ( .pdb) 檔中抓取這些檔案。 如果缺少這些值，DIA 就無法計算相對的虛擬位址，而且 [IDiaAddressMap：： get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) 方法會傳回 `FALSE` 。 接著，用戶端必須呼叫 [IDiaAddressMap：:p ut_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) 方法，以便在從映射本身提供遺漏的映射標頭之後，啟用相對虛擬位址計算。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap：： set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap：： get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)
