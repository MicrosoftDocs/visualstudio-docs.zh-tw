---
title: "Idiaframedata:: Execute |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8ad08fd9800fdc197d4218fa55c83487e132f25d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
執行堆疊回溯，並傳回結果的堆疊查核行程框架介面中。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### <a name="parameters"></a>參數  
 `frame`  
 [in][IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)保存框架暫存器之狀態的物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。 下表顯示可能的傳回值，這個方法。  
  
|值|描述|  
|-----------|-----------------|  
|E_DIA_INPROLOG|無法執行序言程式碼中的堆疊框架。|  
|E_DIA_SYNTAX|剖析框架程式中發生錯誤。|  
|E_DIA_FRAME_ACCESS|無法存取暫存器或記憶體。|  
|E_DIA_VALUE|計算的值 （例如，除以零） 時發生錯誤。|  
  
## <a name="remarks"></a>備註  
 若要回溯堆疊偵錯期間呼叫這個方法。 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)物件由用戶端應用程式接收到暫存器的更新，並提供所使用的方法實作`execute`方法。  
  
## <a name="see-also"></a>請參閱  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)