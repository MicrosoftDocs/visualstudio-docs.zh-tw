---
title: 效能工具使用者入門 | Microsoft Docs
description: 瞭解 Visual Studio 提供的不同方式，以收集、查看和分析程式碼效能資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2018
ms.topic: conceptual
helpviewer_keywords:
- getting started, performance
- getting started, profiling tools
ms.assetid: 02085214-a8e4-40fd-9b26-32391a7a7082
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1eb65e3cb8273f36cd9255bc0a3a2f8e91689f39
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907368"
---
# <a name="getting-started-with-performance-tools"></a>效能工具使用者入門

Visual Studio 提供數種方式供您收集、檢視和分析程式碼效能資料。 在許多情況下，最佳的效能工具使用者入門方式是使用 [效能精靈] 的預設設定。 該精靈會收集應用程式統計資料，以協助您找出程式碼中的效能問題。

- Visual Studio [錯誤清單] 視窗中會顯示效能警告，以通知您常見的程式碼撰寫問題。 您可以從警告巡覽至您的原始程式碼，以及可協助您撰寫更有效率程式碼的詳細說明主題。

- 效能報告可讓您檢視應用程式結構的不同層級、原始程式碼行及處理序。 效能報告會顯示應用程式執行資料，舉凡特定函式的呼叫函式及所呼叫函式，或是整個應用程式的呼叫樹狀結構。

若要快速分析專案、應用程式或 ASP.NET 網站，請選取 [ **Debug**  >  **效能分析工具**]，然後選取 [**效能分析]**。 如需詳細指示，請參閱[效能分析的初學者指南](../profiling/beginners-guide-to-cpu-sampling.md)和[如何：收集網站的效能資料](../profiling/how-to-collect-performance-data-for-a-web-site.md)。

若要手動指定和設定效能分析會話，請選取 [ **Debug**  >  **Profiler**  >  **效能總管**]。 使用 [效能總管] 中的 [目標] 資料夾和 [屬性] 頁面以設定工作階段。 如需指示，請參閱[如何：手動建立效能工作階段](../profiling/how-to-manually-create-performance-sessions.md)。

**另請參閱：**

- [效能工具概觀](../profiling/overviews-performance-tools.md)
- [分析效能工具資料](../profiling/analyzing-performance-tools-data.md)
- [使用效能規則分析資料](../profiling/using-performance-rules-to-analyze-data.md)
- [設定效能工作階段](../profiling/configuring-performance-sessions.md)
