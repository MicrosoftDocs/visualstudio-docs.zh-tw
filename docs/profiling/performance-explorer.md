---
title: 效能總管 | Microsoft Docs
description: 瞭解 Visual Studio 分析工具如何讓開發人員測量、評估及鎖定程式碼中與效能相關的問題。
ms.date: 06/19/2017
ms.topic: conceptual
f1_keywords:
- vs.performance
- vs.performance.wizard.website
helpviewer_keywords:
- performance tools [Visual Studio ALM]
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 401b054c6bfa7ed2bee376c260a3eb3843d6f1c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922302"
---
# <a name="performance-explorer"></a>效能總管

Visual Studio 程式碼剖析工具可讓開發人員測量、評估和標定程式碼中與效能有關的問題。 這些工具已經完全整合到 IDE，藉此提供順暢無礙又平易近人的使用者體驗。

分析應用程式相當簡單。 您可以從建立新的效能工作階段開始。 在 Visual Studio Team System Development Edition 中，您可以使用 [效能工作階段精靈] 建立新的效能工作階段。 在效能工作階段結束後，在分析期間收集的資料會儲存在 .*vsp* 檔中。 您可以在 IDE 中檢視 .*vsp* 檔。 還有幾種報告檢視，可協助您從蒐集的資料中視覺化及偵測效能問題。

也可以從命令列使用分析工具。 這可以讓使用者能夠彈性地從命令列執行這些工具，或是用這些工具來自動化使用指令碼的作業。

如需與效能及分析相關之目前和進階主題的詳細資訊，請搜尋 Microsoft Developer Network 上的主題和 Microsoft 部落格。 請使用 Enterprise Performance Tools Team 做為搜尋關鍵字。

## <a name="common-tasks"></a>常見工作

|Task|相關內容|
|----------|---------------------|
|**Windows 8 和更新版本的技術**|[Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)|
|**了解分析概念：** 了解使用 [程式碼剖析工具] 收集、檢視及分析程式碼效能時所採用的概念和字彙。|[概觀](../profiling/overviews-performance-tools.md)|
|**一頭栽入並執行：** 了解使用 [程式碼剖析工具] 收集、檢視及分析程式碼效能時所採用的基本程序。 請依照實習的逐步解說動手嘗試。|[開始使用](../profiling/getting-started-with-performance-tools.md)|
|**設定程式碼分析工作階段：** 了解如何指定要進行分析的專案或二進位檔、選取分析方法、選擇要收集的效能資料，以及如何設定其他分析工作階段選項等進階方法。|[設定效能工作階段](../profiling/configuring-performance-sessions.md)|
|**控制程式碼分析工具收集的資料：** 了解如何使用效能工作階段屬性和互動程序來開始和停止分析，以及如何將收集的效能資料限制在您所要的資訊。|[控制資料收集](../profiling/controlling-data-collection.md)|
|**找出效能問題：** 了解如何在 [程式碼剖析工具報表] 檢視視窗中檢視和分析收集到的效能資料。|[分析效能工具資料](../profiling/analyzing-performance-tools-data.md)|
|**分析效能變更：** 了解如何比較兩個分析工具資料檔案，以分析效能的變化。|[比較效能資料檔案](../profiling/comparing-performance-data-files.md)|
|**儲存及共用您的結果：** 了解如何儲存分析資料以供封存或共用。|[儲存和匯出效能工具資料](../profiling/saving-and-exporting-performance-tools-data.md)|
|**自動化分析：** 了解如何從命令提示字元使用 [程式碼剖析工具]。|[從命令列分析](../profiling/using-the-profiling-tools-from-the-command-line.md)|
|**以程式設計方式控制程式碼分析：** 了解如何使用 Managed 和原生程式碼剖析工具應用程式開發介面，直接從原始程式碼控制資料收集。|[程式碼剖析工具 API](../profiling/profiling-tools-apis.md)|
|**疑難排解分析問題**|[針對效能工具問題進行疑難排解](../profiling/troubleshooting-performance-tools-issues.md)|

## <a name="see-also"></a>另請參閱

[初步認識分析工具](../profiling/profiling-feature-tour.md)
