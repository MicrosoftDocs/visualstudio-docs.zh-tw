---
title: 偵錯介面存取 SDK |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 319c509ac293b4f55ab574a5f29cdbd23709ebaa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47484725"
---
# <a name="debug-interface-access-sdk"></a>偵錯 (偵錯介面存取 SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[Debug Interface Access SDK](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk)。  
  
Microsoft 偵錯介面存取軟體開發套件 (DIA SDK) 提供的偵錯資訊儲存在 Microsoft 讓工具所產生的程式資料庫 (.pdb) 檔案的存取。 讓工具所產生的.pdb 檔案的格式進行常數的修訂，因為公開格式是不切實際的。 您可以使用 DIA API，來開發應用程式的搜尋和瀏覽儲存在.pdb 檔案中的偵錯資訊。 比方說，這類應用程式可以報告堆疊往回追蹤資訊，並分析效能資料。  
  
## <a name="in-this-section"></a>本節內容  
 [快速入門](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
 概述 DIA SDK 功能，並指定 DIA SDK 以及必要的標頭和程式庫檔案的安裝位置。  
  
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



