---
title: 'Idiaframedata:: Get_functionstart |Microsoft Docs'
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
- IDiaFrameData::get_functionStart method
ms.assetid: 49fd24fb-65c2-4812-8303-56a968353e1b
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e0a39212fd93138444c6aa412071cec4894b0667
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812682"
---
# <a name="idiaframedatagetfunctionstart"></a>IDiaFrameData::get_functionStart
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

擷取指出區塊是否包含函式的進入點的旗標。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT get_functionStart (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]會傳回`TRUE`如果區塊包含進入點; 否則會傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 可以針對不是函式開頭，因為畫面格代表內嵌方法或函式所插入的函式的堆疊框架。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)



