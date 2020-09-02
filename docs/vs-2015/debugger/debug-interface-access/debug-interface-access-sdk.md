---
title: Debug Interface Access SDK |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ddaea95bc879364de99c0ec01213cda30fa4e7d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197614"
---
# <a name="debug-interface-access-sdk"></a>偵錯 (偵錯介面存取 SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Microsoft Debug Interface Access Software 開發工具組 (DIA SDK) 可存取儲存在程式資料庫中的偵錯工具資訊 ( .pdb) Microsoft postcompiler tools 所產生的檔案。 由於 postcompiler 工具所產生的 .pdb 檔案格式會進行不斷的修訂，所以公開格式並不實用。 您可以使用 DIA API 來開發應用程式，以搜尋和流覽儲存在 .pdb 檔案中的 debug 資訊。 例如，這類應用程式可以報告堆疊追蹤資訊，以及分析效能資料。  
  
## <a name="in-this-section"></a>本節內容  
 [快速入門](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
 概述 DIA SDK 功能，並指定安裝 DIA SDK 的位置，以及必要的標頭檔和程式庫檔案。  
  
 [查詢 .Pdb 檔案](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 提供有關如何使用 DIA API 來查詢 .pdb 檔案的指示。  
  
 [符號和符號標記](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
 討論如何在 DIA API 中使用符號和符號標記。  
  
 [參考](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
 包含 DIA API 的介面、方法、列舉和結構。  
  
 [Dia2dump 範例](../../debugger/debug-interface-access/dia2dump-sample.md)  
 說明如何使用 DIA API 來搜尋和流覽 debug 資訊。  
  
 [Dia2dump.cpp 原始程式檔](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)  
 [Dia2dump 範例](../../debugger/debug-interface-access/dia2dump-sample.md)用來示範 DIA API 的原始程式碼。
