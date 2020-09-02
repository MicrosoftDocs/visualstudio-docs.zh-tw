---
title: 堆積配置函式的 Debug 版本 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- debugging [CRT], heap allocation functions
- debugging memory leaks, CRT debug library functions
- malloc function
- memory leaks, CRT debug library functions
- heap allocation, debug
- _malloc_dbg function
ms.assetid: 91748bdc-f4cd-4d8b-ab98-0493dab7ed0d
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 13f8d8b79ecf586048aacf3cd9442c596f184be3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691163"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>堆積配置函式的偵錯版本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C 執行階段程式庫包含堆積配置 (Heap Allocation) 函式的特殊偵錯版本。 這些函式的名稱與發行版本相同，再加上「_dbg」。 本主題以 `malloc` 和 `_malloc_dbg` 為例，說明 CRT 函式發行版本和 _dbg 版本之間的差異。  
  
 當定義 [_DEBUG](https://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a) 時，CRT 會將所有 [malloc](https://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0) 呼叫對應至 [_malloc_dbg](https://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb)。 因此，您在偵錯時不需要改用 `_malloc_dbg` 取代 `malloc`，來重寫程式碼取得這些功能。  
  
 然而，您可能要明確地呼叫 `_malloc_dbg`。 明確地呼叫 `_malloc_dbg` 會多出下列一些優點：  
  
- 追蹤 `_CLIENT_BLOCK` 類型配置。  
  
- 儲存發生配置要求位置的原始程式檔和行號。  
  
  如果您不想要將呼叫轉換成 `malloc` `_malloc_dbg` ，可以藉由定義 [_CRTDBG_MAP_ALLOC](https://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b)來取得原始程式檔資訊，這會導致預處理器直接將的所有呼叫對應 `malloc` 至， `_malloc_dbg` 而不是依賴包裝 `malloc` 函式。  
  
  若要追蹤用戶端區塊裡不同類型的配置，您必須直接呼叫 `_malloc_dbg` 並且將 `blockType` 參數設為 `_CLIENT_BLOCK`。  
  
  未定義 _DEBUG 時，不 `malloc` 會干擾的呼叫，呼叫 `_malloc_dbg` 會解析為，系統會 `malloc` 忽略 [_CRTDBG_MAP_ALLOC](https://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b) 的定義，而且不會提供與配置要求有關的原始程式檔資訊。 因為 `malloc` 沒有區塊型別參數，`_CLIENT_BLOCK` 類型的要求會被當成標準配置處理。  
  
## <a name="see-also"></a>另請參閱  
 [CRT 偵錯技術](../debugger/crt-debugging-techniques.md)
