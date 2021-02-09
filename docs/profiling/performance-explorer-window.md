---
title: 效能總管視窗 | Microsoft Docs
description: 瞭解 Visual Studio IDE 中的效能總管視窗如何讓您使用 Visual Studio 分析工具設定效能會話。
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performanceexplorer
- vs.performance.explorer
helpviewer_keywords:
- performance tools, Performance Explorer
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4533bcb59ebbd36f47ddf73f9b78429f041c357c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922326"
---
# <a name="performance-explorer-window"></a>效能總管視窗

Visual Studio IDE 中的 [效能總管] 視窗可讓您使用 Visual Studio 分析工具來設定和啟動效能工作階段。 如果您需要開啟視窗，請遵循[效能分析的初級開發人員指南](../profiling/beginners-guide-to-cpu-sampling.md)中的指示。

## <a name="performance-explorer-toolbar"></a>效能總管工具列

下列選項位於 [效能總管] 工具列上：

- **啟動效能精靈** - 顯示將新的效能工作階段加入 [效能總管] 視窗的 [效能精靈]。

- **新增效能工作階段** - 將空白的效能工作階段加入 [效能總管] 視窗。

- **啟動** - [啟動] 命令按鈕清單可讓您啟動立即啟用分析 ([啟動並啟用程式碼剖析]) 或暫停分析 ([啟動並暫停程式碼剖析]) 的目標應用程式。

- **方法** - 指定工作階段的程式碼剖析方法是取樣或檢測。

- **停止** - 立即結束目標應用程式和程式碼剖析工具。

- **附加/中斷連結** - 顯示 [將程式碼剖析工具附加至處理序] 對話方塊，供您選取一個執行中的處理序以附加程式碼剖析工具。

## <a name="performance-explorer-window"></a>效能總管視窗

[效能總管] 視窗包含樹狀目錄控制項，其中顯示一或多個效能工作階段的二進位檔和報表資料檔案。

- **工作階段名稱** - 樹狀目錄控制項的根目錄，其中包含工作階段名稱。 以滑鼠右鍵按一下工作階段名稱可設定工作階段屬性，或啟動目標應用程式和程式碼剖析工具。

- **目標** - 顯示要在工作階段中進行程式碼剖析的二進位檔的名稱。 以滑鼠右鍵按一下 [目標] 來新增或移除二進位檔、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 專案或網站。 以滑鼠右鍵按一下目標名稱以設定個別二進位檔的屬性。

- **報表** - 顯示針對工作階段產生的程式碼剖析工具資料檔案的名稱。 以滑鼠右鍵按一下 [報表] 以加入現有的報表，或比較兩個程式碼剖析工具資料檔案。 以滑鼠右鍵按一下報表名稱以開啟、移除或匯出程式碼剖析工具資料檔案。

## <a name="see-also"></a>另請參閱

[概覽](../profiling/overviews-performance-tools.md) 
設定[效能會話](../profiling/configuring-performance-sessions.md) 
[控制資料收集](../profiling/controlling-data-collection.md)
