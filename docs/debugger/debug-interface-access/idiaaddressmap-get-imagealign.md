---
title: 'Idiaaddressmap:: Get_imagealign |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_imageAlign method
ms.assetid: f1ba8071-669c-4cf7-9ac0-02f26d99f366
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bd085e59606b1e8598359636208cf308ff0b711d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31459070"
---
# <a name="idiaaddressmapgetimagealign"></a>IDiaAddressMap::get_imageAlign
擷取目前的影像對齊。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_imageAlign (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回可執行檔的影像對齊值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 根據映像已載入而且建立方式的特定記憶體界限對齊映像。 對齊方式，通常是 1、 2、 4、 8、 16、 32 或 64 位元組界限上。 可以設定的影像對齊方式，藉由呼叫[idiaaddressmap:: Put_imagealign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)