---
title: "Idiasegment:: Get_execute |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSegment::get_execute method
ms.assetid: 746cdf8e-9097-415d-ba10-069854153185
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1290218bdef89f9e96ac68623ba72e83455acc10
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiasegmentgetexecute"></a>IDiaSegment::get_execute
擷取指出區段是否為可執行檔的旗標。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_execute (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回`TRUE`如果區段已標記為可執行檔，否則傳回`FALSE`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)