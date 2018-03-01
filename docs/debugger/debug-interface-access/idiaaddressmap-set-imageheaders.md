---
title: "Idiaaddressmap:: Set_imageheaders |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 74556e2e67478cef9b495d3740dc910b62cc8293
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiaaddressmapsetimageheaders"></a>IDiaAddressMap::set_imageHeaders
設定影像啟用相對虛擬位址轉譯的標頭。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT set_imageHeaders (   
   DWORD cbData,  
   BYTE  data[],  
   BOOL  originalHeaders  
);  
```  
  
#### <a name="parameters"></a>參數  
 cbData  
 [in]標頭資料的位元組數。 必須是`n*sizeof(IMAGE_SECTION_HEADER)`其中`n`是可執行檔中的區段標頭數目。  
  
 [資料]  
 [in]陣列`IMAGE_SECTION_HEADER`来做為映像標頭的結構。  
  
 originalHeaders  
 [in]設定為`FALSE`從新的映像的映像標頭是否`TRUE`如果它們反映在升級之前的原始映像。 一般而言，這會設定為`TRUE`只有在搭配呼叫[idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)方法。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 `IMAGE_SECTION_HEADER`結構會在 Winnt.h 中宣告與表示可執行檔映像區段標頭的格式。  
  
 取決於相對虛擬位址計算`IMAGE_SECTION_HEADER`值。 通常，DIA 擷取這些程式資料庫 (.pdb) 檔案。 如果這些值會遺失，就無法計算相對虛擬位址 DIA 和[idiaaddressmap:: Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)方法會傳回`FALSE`。 用戶端必須再呼叫[idiaaddressmap:: Put_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)方法，才能提供從本身的映像缺少映像標頭之後的相對虛擬位址計算。  
  
## <a name="see-also"></a>請參閱  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [Idiaaddressmap:: Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)