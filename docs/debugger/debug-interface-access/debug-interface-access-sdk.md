---
title: 偵錯介面存取 SDK |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ae5afe3b5eacaad31ae7b4fcd6aeb092aa37300c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="debug-interface-access-sdk"></a>偵錯 (偵錯介面存取 SDK)
Microsoft 偵錯介面存取軟體開發套件 (DIA SDK) 提供存取偵錯資訊儲存在 Microsoft 讓工具所產生的程式資料庫 (.pdb) 檔。 .Pdb 檔案，讓工具所產生的格式會經歷常數修訂，因為公開格式是不可行的。 使用 DIA API 時，您可以開發應用程式，搜尋並瀏覽儲存在.pdb 檔案中的偵錯資訊。 這類應用程式，例如無法，堆疊追蹤回資訊報告和分析效能資料。  
  
## <a name="in-this-section"></a>本節內容  
 [快速入門](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
 概略 DIA SDK 功能，並指定 DIA SDK 安裝以及必要的標頭和程式庫檔案的位置。  
  
 [查詢 .Pdb 檔案](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 提供如何使用 DIA API 來查詢.pdb 檔案的指示。  
  
 [符號和符號標記](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
 討論如何在 DIA API 中使用符號和符號標記。  
  
 [參考資料](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
 包含介面、 方法、 列舉和結構的 DIA API。  
  
 [Dia2dump 範例](../../debugger/debug-interface-access/dia2dump-sample.md)  
 說明如何使用 DIA API 來搜尋和瀏覽偵錯資訊。  
  
 [Dia2dump.cpp 原始程式檔](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)  
 來源所使用的程式碼[Dia2dump 範例](../../debugger/debug-interface-access/dia2dump-sample.md)示範 DIA API。