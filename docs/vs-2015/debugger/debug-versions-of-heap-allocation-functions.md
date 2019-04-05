---
title: 偵錯版本的堆積配置函式 |Microsoft Docs
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
ms.openlocfilehash: 26d81d7b2aaa3bd8661e0da4b1590e9c8c0d0191
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940364"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>堆積配置函式的偵錯版本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C 執行階段程式庫包含堆積配置 (Heap Allocation) 函式的特殊偵錯版本。 這些函式的名稱與發行版本相同，再加上「_dbg」。 本主題以 `malloc` 和 `_malloc_dbg` 為例，說明 CRT 函式發行版本和 _dbg 版本之間的差異。  
  
 當[_DEBUG](http://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a)是定義，CRT 對應至所有[malloc](http://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0)呼叫[_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb)。 因此，您在偵錯時不需要改用 `_malloc_dbg` 取代 `malloc`，來重寫程式碼取得這些功能。  
  
 然而，您可能要明確地呼叫 `_malloc_dbg`。 明確地呼叫 `_malloc_dbg` 會多出下列一些優點：  
  
- 追蹤 `_CLIENT_BLOCK` 類型配置。  
  
- 儲存發生配置要求位置的原始程式檔和行號。  
  
  如果您不想要轉換您`malloc`呼叫`_malloc_dbg`，您可以藉由定義取得來源檔案資訊[_CRTDBG_MAP_ALLOC](http://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b)，這會讓前置處理器直接對應到所有呼叫`malloc`至`_malloc_dbg`而不是依賴周圍的包裝函式`malloc`。  
  
  若要追蹤用戶端區塊裡不同類型的配置，您必須直接呼叫 `_malloc_dbg` 並且將 `blockType` 參數設為 `_CLIENT_BLOCK`。  
  
  未定義 _DEBUG，呼叫`malloc`不干擾，呼叫`_malloc_dbg`會解析為`malloc`，定義[_CRTDBG_MAP_ALLOC](http://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b)會忽略，而來源相關的檔案資訊未提供配置要求。 因為 `malloc` 沒有區塊型別參數，`_CLIENT_BLOCK` 類型的要求會被當成標準配置處理。  
  
## <a name="see-also"></a>另請參閱  
 [CRT 偵錯技術](../debugger/crt-debugging-techniques.md)
