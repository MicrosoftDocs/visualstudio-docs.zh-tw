---
title: 用戶端區塊攔截函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eccc1781174394da333d2fc703fec0b4d31e522a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="client-block-hook-functions"></a>用戶端區塊攔截函式
如果您要驗證或報告儲存在 `_CLIENT_BLOCK` 區塊裡的資料內容，您可以撰寫符合這個目的的函式。 您所撰寫的函式，必須與下列在 CRTDBG.H 裡定義的原型類似：  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 換句話說，您攔截函式應該接受**void**配置的連同區塊的開頭的指標**size_t**輸入值，指出配置的大小，並傳回`void`. 除此之外，其他的內容則由您決定。  
  
 一旦您已安裝您的攔截函式使用[_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient)，它會呼叫每次`_CLIENT_BLOCK`區塊傾印。 然後您可以使用[_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)以取得資訊的傾印區塊的子類型的類型。  
  
 您傳遞給函式指標`_CrtSetDumpClient`的型別 **_CRT_DUMP_CLIENT**、 CRTDBG 中所定義。H:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>另請參閱  
 [偵錯攔截函式寫入](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 範例](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)