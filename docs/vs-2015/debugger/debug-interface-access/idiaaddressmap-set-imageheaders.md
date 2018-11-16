---
title: 'Idiaaddressmap:: Set_imageheaders |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f3e2504030d3e8f28c1a41dea1c053c7e1deb1bf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810230"
---
# <a name="idiaaddressmapsetimageheaders"></a>IDiaAddressMap::set_imageHeaders
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

設定映像標頭，以啟用相對虛擬位址轉譯。  
  
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
 [in]標頭資料的位元組數目。 必須是`n*sizeof(IMAGE_SECTION_HEADER)`其中`n`是可執行檔中區段標頭數目。  
  
 [資料]  
 [in]陣列`IMAGE_SECTION_HEADER`結構，以用作映像標頭。  
  
 originalHeaders  
 [in]設定為`FALSE`從新的映像，映像標頭是否`TRUE`如果它們反映原始的映像，再升級。 一般而言，這會設定為`TRUE`只有在搭配呼叫[idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)方法。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 `IMAGE_SECTION_HEADER`結構會在 Winnt.h 中宣告和表示的可執行檔映像區段標頭的格式。  
  
 相對虛擬位址計算相依於`IMAGE_SECTION_HEADER`值。 通常，DIA 擷取從程式資料庫 (.pdb) 檔案。 如果這些值遺漏，DIA 是無法計算相對虛擬位址並[idiaaddressmap:: Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)方法會傳回`FALSE`。 用戶端必須再呼叫[idiaaddressmap:: Put_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)方法，以提供遺漏的映像標頭中，從映像本身之後啟用的相對虛擬位址計算。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [Idiaaddressmap:: Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)



