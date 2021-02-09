---
title: CRT 調試技術 |Microsoft Docs
description: 您可以使用各種技術來對使用 C 執行時間 (CRT) 程式庫的程式進行程式設計。 您可以使用本文及其連結來瞭解這類技術。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 84d5f85584403cc18cd00708a8d4698723d614ef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857606"
---
# <a name="crt-debugging-techniques"></a>CRT 偵錯技術
如果您要偵錯的程式使用 C 執行階段程式庫，可以使用這些偵錯技術。

## <a name="in-this-section"></a>本節內容
 [CRT Debug 程式庫使用](../debugger/crt-debug-library-use.md)

 描述由 C 執行階段程式庫提供的偵錯支援，並提供存取這些工具的指示。

 [報告的宏](../debugger/macros-for-reporting.md)

 提供 **_RPTn** 和 **_RPTFn** 巨集 (定義於 CRTDBG.H) 的相關資訊，這些巨集取代偵錯時使用的 `printf` 陳述式。

 [堆積配置函數的偵錯工具版本](../debugger/debug-versions-of-heap-allocation-functions.md)

 討論堆積配置函式的特殊偵錯版本，包括：CRT 對應呼叫的方式、明確呼叫他們的優點、如何避免轉換、追蹤用戶端區塊中不同的配置類型，以及未定義 _DEBUG 的結果。

 [CRT Debug 堆積詳細資料](../debugger/crt-debug-heap-details.md)

 提供記憶體管理和偵錯堆積、偵錯堆積上的區塊類型、使用偵錯堆積、回報函式的堆積狀態和追蹤堆積配置要求的連結。

 [調試攔截函式寫入](../debugger/debug-hook-function-writing.md)

 列出以下主題的連結：用戶端區塊攔截函式、配置攔截函式，配置攔截與 CRT 記憶體配置，以及報告攔截函式。

 [使用 CRT 程式庫尋找記憶體遺漏](../debugger/finding-memory-leaks-using-the-crt-library.md)

 說明使用偵錯工具和 C 執行階段程式庫來偵錯和找出記憶體流失問題的技術。

## <a name="related-sections"></a>相關章節

- [偵錯工具代碼](../debugger/debugging-native-code.md) -討論 C 和 c + + 應用程式的一些常見的偵錯工具問題和技術。
- [偵錯工具安全性](../debugger/debugger-security.md) ：提供更安全的偵測建議。