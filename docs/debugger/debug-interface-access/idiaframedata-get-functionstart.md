---
title: 'Idiaframedata:: Get_functionstart |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_functionStart method
ms.assetid: 49fd24fb-65c2-4812-8303-56a968353e1b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 28dbb603bab183a666d4d0efa6419b1c10b17a6a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53864211"
---
# <a name="idiaframedatagetfunctionstart"></a>IDiaFrameData::get_functionStart
擷取指出區塊是否包含函式的進入點的旗標。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_functionStart (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]會傳回`TRUE`如果區塊包含進入點; 否則會傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 可以針對不是函式開頭，因為畫面格代表內嵌方法或函式所插入的函式的堆疊框架。  
  
## <a name="see-also"></a>請參閱  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)