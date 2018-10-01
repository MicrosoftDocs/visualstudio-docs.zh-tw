---
title: 用戶端區塊攔截函式 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29bbfb24566a59047e47090f92a040c3c2fe8a12
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47489114"
---
# <a name="client-block-hook-functions"></a>用戶端區塊攔截函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[用戶端區塊攔截函式](https://docs.microsoft.com/visualstudio/debugger/client-block-hook-functions)。  
  
如果您要驗證或報告儲存在 `_CLIENT_BLOCK` 區塊裡的資料內容，您可以撰寫符合這個目的的函式。 您所撰寫的函式，必須與下列在 CRTDBG.H 裡定義的原型類似：  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 換句話說，您攔截函式應該接受**void**指標至配置區塊的開頭**size_t**輸入值，指出的配置大小，並傳回`void`. 除此之外，其他的內容則由您決定。  
  
 一旦您已安裝您的攔截函式使用[_CrtSetDumpClient](http://msdn.microsoft.com/library/f3dd06d0-c331-4a12-b68d-25378d112033)，則會呼叫每次`_CLIENT_BLOCK`區塊傾印。 然後您可以使用[_CrtReportBlockType](http://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b)以取得有關的型別或傾印區塊的子類型。  
  
 您傳遞至函式指標`_CrtSetDumpClient`屬於型別 **_CRT_DUMP_CLIENT**、 CRTDBG 中所定義。H:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>另請參閱  
 [撰寫偵錯攔截函式](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 範例](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](http://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b)



