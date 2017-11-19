---
title: "Idiastackframe:: Get_maxstack |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackFrame::get_maxStack method
ms.assetid: 6352e972-7105-4d0e-aeba-b8fc16d62dec
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33dc48e1753595c54e535813a27f70f1b0f9920f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiastackframegetmaxstack"></a>IDiaStackFrame::get_maxStack
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
 如果成功，傳回`S_OK`。 傳回`S_FALSE`不支援的屬性。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)