---
title: "堆積配置函式的偵錯版本 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.crt
dev_langs:
- CSharp
- VB
- FSharp
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
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 63642402f6e98e42b2d4954a6065f61fb61159b5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="debug-versions-of-heap-allocation-functions"></a>堆積配置函式的偵錯版本
C 執行階段程式庫包含堆積配置 (Heap Allocation) 函式的特殊偵錯版本。 這些函式的名稱與發行版本相同，再加上「_dbg」。 本主題以 `malloc` 和 `_malloc_dbg` 為例，說明 CRT 函式發行版本和 _dbg 版本之間的差異。  
  
 當[_DEBUG](/cpp/c-runtime-library/debug)是定義，CRT 對應至所有[malloc](/cpp/c-runtime-library/reference/malloc)呼叫[_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)。 因此，您在偵錯時不需要改用 `_malloc_dbg` 取代 `malloc`，來重寫程式碼取得這些功能。  
  
 然而，您可能要明確地呼叫 `_malloc_dbg`。 明確地呼叫 `_malloc_dbg` 會多出下列一些優點：  
  
-   追蹤 `_CLIENT_BLOCK` 類型配置。  
  
-   儲存發生配置要求位置的原始程式檔和行號。  
  
 如果您不想要轉換您`malloc`呼叫`_malloc_dbg`，您可以藉由定義取得來源檔案資訊[_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc)，因而導致前置處理器直接對應的所有呼叫`malloc`至`_malloc_dbg`而不是依賴周圍的包裝函式`malloc`。  
  
 若要追蹤用戶端區塊裡不同類型的配置，您必須直接呼叫 `_malloc_dbg` 並且將 `blockType` 參數設為 `_CLIENT_BLOCK`。  
  
 未定義 _DEBUG，呼叫`malloc`不干擾，呼叫`_malloc_dbg`會解析為`malloc`，定義[_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc)會被忽略，和原始程式檔相關的資訊未提供配置要求。 因為 `malloc` 沒有區塊類型參數，`_CLIENT_BLOCK` 類型的要求會被當成標準配置處理。  
  
## <a name="see-also"></a>請參閱  
 [CRT 偵錯技術](../debugger/crt-debugging-techniques.md)