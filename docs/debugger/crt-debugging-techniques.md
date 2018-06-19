---
title: CRT 偵錯技術 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- c.runtime.debugging
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [CRT]
- CRT, debugging
- debugging [C++], CRT debug support
ms.assetid: 9be561f6-14a8-44ff-925d-d911d5b8e6ff
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 890dec4a47a4dd49fa75521aaad068d331652a92
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31458423"
---
# <a name="crt-debugging-techniques"></a>CRT 偵錯技術
如果您要偵錯的程式使用 C 執行階段程式庫，可以使用這些偵錯技術。  
  
## <a name="in-this-section"></a>本節內容  
 [CRT 偵錯程式庫操作](../debugger/crt-debug-library-use.md)  
 描述由 C 執行階段程式庫提供的偵錯支援，並提供存取這些工具的指示。  
  
 [報告巨集](../debugger/macros-for-reporting.md)  
 相關資訊提供 **_RPTn**和 **_RPTFn**巨集 （定義於 CRTDBG。H)，取代使用`printf`陳述式中的偵錯。  
  
 [堆積配置函式的偵錯版本](../debugger/debug-versions-of-heap-allocation-functions.md)  
 討論堆積配置函式的特殊偵錯版本，包括：CRT 對應呼叫的方式、明確呼叫他們的優點、如何避免轉換、追蹤用戶端區塊中不同的配置類型，以及未定義 _DEBUG 的結果。  
  
 [CRT 偵錯堆積詳細資料](../debugger/crt-debug-heap-details.md)  
 提供記憶體管理和偵錯堆積、偵錯堆積上的區塊類型、使用偵錯堆積、回報函式的堆積狀態和追蹤堆積配置要求的連結。  
  
 [撰寫偵錯攔截函式](../debugger/debug-hook-function-writing.md)  
 列出以下主題的連結：用戶端區塊攔截函式、配置攔截函式，配置攔截與 CRT 記憶體配置，以及報告攔截函式。  
  
 [使用 CRT 程式庫尋找記憶體遺漏](../debugger/finding-memory-leaks-using-the-crt-library.md)  
 說明使用偵錯工具和 C 執行階段程式庫來偵錯和找出記憶體流失問題的技術。  
  
## <a name="related-sections"></a>相關章節  
 [偵錯機器碼](../debugger/debugging-native-code.md)  
 討論 C 和 C++ 應用程式的一些常見偵錯問題和技巧。  
  
 [偵錯工具安全性](../debugger/debugger-security.md)  
 提供更安全偵錯的建議事項。