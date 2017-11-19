---
title: "Idiaframedata:: Get_maxstack |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaFrameData::get_maxStack method
ms.assetid: 2585e13c-c0f3-49fe-9a84-08adb0dbeaa4
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 086b1db960e8a910e34631a40f125ea5eb4874ba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiaframedatagetmaxstack"></a>IDiaFrameData::get_maxStack
擷取推入堆疊框架中的位元組的數目上限。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_maxStack (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回推送到堆疊上的位元組的數目上限。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法所傳回的值通常用於解譯的程式字串 (請參閱[idiaframedata:: Get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)方法定義的程式字串)。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)