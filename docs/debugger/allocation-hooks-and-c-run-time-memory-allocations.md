---
title: 配置攔截和 C 執行階段記憶體配置 |Microsoft Docs
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
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7e4c631b72ae9b12f77daf2ddd49919651c0b3e5
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433102"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>配置攔截和 C 執行階段記憶體配置
配置攔截函式非常重要的限制是，必須明確地忽略`_CRT_BLOCK`區塊。 這些區塊是由 C 執行階段程式庫函式內部做，如果它們呼叫任何配置內部記憶體的 C 執行階段程式庫函式的記憶體配置。 您可以忽略`_CRT_BLOCK`區塊包含 folloiwng 程式碼，在開始您的配置攔截函式：  
  
```cpp
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 如果配置攔截沒有忽略`_CRT_BLOCK`區塊，那麼攔截任何 C 執行階段程式庫函式可以捕捉無窮迴圈裡的程式。 例如，`printf` 會執行內部配置。 如果您攔截程式碼會呼叫`printf`，則產生的配置會再次呼叫攔截稱之為**printf**一次，依此類推，直到堆疊溢位。 如果您要報告 `_CRT_BLOCK` 配置操作，避開這種限制的一種方法是使用 Windows API 函式，而不是執行階段函式來執行格式化和輸出。 Windows Api 不使用 C 執行階段程式庫堆積，因為它們不會捕捉配置攔截永無止盡的迴圈中。  
  
 如果您檢查執行階段程式庫原始程式檔時，您會看到，預設配置攔截函式**CrtDefaultAllocHook** (只簡單傳回 **，則為 TRUE**)，位於個別的檔案，DBGHOOK。C。 如果您想要呼叫甚至會在您的應用程式前執行的執行階段啟始程式碼所做的配置中的配置攔截**主要**函式，您可以使用您自己，而不是取代這個預設函式使用[_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook)。  
  
## <a name="see-also"></a>另請參閱  
 [撰寫偵錯攔截函式](../debugger/debug-hook-function-writing.md)   
