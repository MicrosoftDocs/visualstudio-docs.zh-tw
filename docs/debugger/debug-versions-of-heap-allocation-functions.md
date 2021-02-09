---
title: 堆積配置函式的 Debug 版本 |Microsoft Docs
description: 使用 C 執行時間程式庫中堆積配置函式的偵錯工具版本。 這些函式的名稱與發行版本相同，並附加 _dbg。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9eedf9259f7bc62f32ca563d863a7fb686b8f6f2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873115"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>堆積配置函式的偵錯版本
C 執行階段程式庫包含堆積配置 (Heap Allocation) 函式的特殊偵錯版本。 這些函式的名稱與發行版本相同，再加上「_dbg」。 本主題以 `malloc` 和 `_malloc_dbg` 為例，說明 CRT 函式發行版本和 _dbg 版本之間的差異。

 當定義 [_DEBUG](/cpp/c-runtime-library/debug) 時，CRT 會將所有 [malloc](/cpp/c-runtime-library/reference/malloc) 呼叫對應至 [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)。 因此，您在偵錯時不需要改用 `_malloc_dbg` 取代 `malloc`，來重寫程式碼取得這些功能。

 然而，您可能要明確地呼叫 `_malloc_dbg`。 明確地呼叫 `_malloc_dbg` 會多出下列一些優點：

- 追蹤 `_CLIENT_BLOCK` 類型配置。

- 儲存發生配置要求位置的原始程式檔和行號。

  如果您不想要將呼叫轉換成 `malloc` `_malloc_dbg` ，可以藉由定義 [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc)來取得原始程式檔資訊，這會導致預處理器直接將的所有呼叫對應 `malloc` 至， `_malloc_dbg` 而不是依賴包裝 `malloc` 函式。

  若要追蹤用戶端區塊裡不同類型的配置，您必須直接呼叫 `_malloc_dbg` 並且將 `blockType` 參數設為 `_CLIENT_BLOCK`。

  未定義 _DEBUG 時，不 `malloc` 會干擾的呼叫，呼叫 `_malloc_dbg` 會解析為，系統會 `malloc` 忽略 [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc) 的定義，而且不會提供與配置要求有關的原始程式檔資訊。 因為 `malloc` 沒有區塊型別參數，`_CLIENT_BLOCK` 類型的要求會被當成標準配置處理。

## <a name="see-also"></a>另請參閱

- [CRT 調試技術](../debugger/crt-debugging-techniques.md)