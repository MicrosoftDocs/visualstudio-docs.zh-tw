---
title: "Idiaimagedata:: Get_imagebase |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: daaaf26e0a33ce8e90b2b8ac621ed47d299c8276
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiaimagedatagetimagebase"></a>IDiaImageData::get_imageBase
擷取映像應該為基礎的記憶體位置。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_imageBase (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回建議的映像基底值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 映像基底的衝突，因為映像可能會被重定基底自動未使用的記憶體位置載入時將它。 這個方法會傳回已儲存在模組中，在編譯時期的基底提示 （建議的記憶體位置）。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)