---
title: 用戶端區塊攔截函式 |Microsoft Docs
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
ms.openlocfilehash: 837307ac97cf52ff8d7073eaab54ec934d446eab
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279306"
---
# <a name="client-block-hook-functions"></a>用戶端區塊攔截函式
如果您要驗證或報告儲存在 `_CLIENT_BLOCK` 區塊裡的資料內容，您可以撰寫符合這個目的的函式。 您所撰寫的函式，必須與下列在 CRTDBG.H 裡定義的原型類似：  
  
```cpp
void YourClientDump(void *, size_t)  
  
```  
  
 換句話說，您攔截函式應該接受**void**指標至配置區塊的開頭**size_t**輸入值，指出的配置大小，並傳回`void`. 除此之外，其他的內容則由您決定。  
  
 一旦您已安裝您的攔截函式使用[_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient)，則會呼叫每次`_CLIENT_BLOCK`區塊傾印。 然後您可以使用[_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)以取得有關的型別或傾印區塊的子類型。  
  
 您傳遞至函式指標`_CrtSetDumpClient`屬於型別 **_CRT_DUMP_CLIENT**、 CRTDBG 中所定義。H:  
  
```cpp
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>另請參閱  
 [撰寫偵錯攔截函式](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 範例](https://msdn.microsoft.com/library/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)
