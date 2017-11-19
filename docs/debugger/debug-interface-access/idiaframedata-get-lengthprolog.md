---
title: "Idiaframedata:: Get_lengthprolog |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaFrameData::get_lengthProlog method
ms.assetid: 5f042ff1-e74e-430a-be34-d2cf1b18eff2
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bcf3e7feada0ba35e9001ed7b3f17167cdb4de7a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiaframedatagetlengthprolog"></a>IDiaFrameData::get_lengthProlog
擷取的初構程式碼區塊中的位元組數目。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_lengthProlog (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回的初構程式碼的位元組數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 初構程式碼是一串指示會保留暫存器、 設定 CPU 狀態，並建立函式的堆疊。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)