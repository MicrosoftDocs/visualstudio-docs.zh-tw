---
title: 'Idiaaddressmap:: Get_imagealign |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaAddressMap::get_imageAlign method
ms.assetid: f1ba8071-669c-4cf7-9ac0-02f26d99f366
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc731e7d488e759788796300e3be24f50b629593
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47487525"
---
# <a name="idiaaddressmapgetimagealign"></a>IDiaAddressMap::get_imageAlign
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[idiaaddressmap:: Get_imagealign](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaaddressmap-get-imagealign)。  
  
擷取目前的影像對齊方式。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_imageAlign (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回可執行檔的影像對齊值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 根據如何映像已載入，並且建立的特定記憶體界限對齊映像。 對齊方式通常是 1、 2、 4、 8、 16、 32 或 64 位元組界限上。 可以設定的影像對齊方式，藉由呼叫[idiaaddressmap:: Put_imagealign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)



