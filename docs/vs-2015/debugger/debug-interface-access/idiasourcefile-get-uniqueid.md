---
title: 'Idiasourcefile:: Get_uniqueid |Microsoft Docs'
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
- IDiaSourceFile::get_uniqueId method
ms.assetid: e0b8dbc0-6061-4f31-bead-2cd72be44e41
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: adfd0bbdd7b6fd29261541f71f718862b96f7f5f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51739785"
---
# <a name="idiasourcefilegetuniqueid"></a>IDiaSourceFile::get_uniqueId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取都是唯一的這個映像的簡單的整數值。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_uniqueId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回簡單的整數的金鑰值，都是唯一的這個映像。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 比較索引鍵，而不是字串可以加速行數字處理。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)



