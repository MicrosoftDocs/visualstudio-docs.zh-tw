---
title: 收集執行緒 & 處理並行資料
description: 流量分析工具並行分析方法，收集導致函式等候資源存取的每個同步處理事件的相關資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c1f6d0dbc8c10c972957e2bcf8092d145bb3651c
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533741"
---
# <a name="collect-thread-and-process-concurrency-data"></a>收集執行緒和處理序並行資料

Visual Studio 分析工具的並行分析方法可讓您收集資源爭用資料，包括會造成所分析應用程式中函式等候存取資源的每個同步處理事件相關資訊。

您可以使用下列其中一種程序來指定並行分析方法：

- 在分析精靈的第一個頁面上，按一下 [並行]。
- 在效能工作階段 [屬性] 對話方塊中的 [一般] 頁面上，按一下 [並行]。
- 在 [效能總管] 工具列的 [方法] 清單中，按一下 [並行]。

## <a name="common-tasks"></a>常見工作

您可以在效能會話的 [_效能會話_]**屬性頁** 對話方塊中指定其他選項。 若要開啟此對話方塊：

- 在 **效能總管** 中，以滑鼠右鍵按一下效能工作階段名稱，然後按一下 [屬性] 。

下表中的工作說明當您使用並行方法進行分析時，可以在 [效能工作階段屬性頁] 對話方塊中指定的選項。

|工作|相關內容|
|----------|---------------------|
|在 [一般] 頁面上，指定產生的分析資料 (.vsp) 檔案的命名詳細資料。|- [如何：設定效能資料檔案名稱選項](../profiling/how-to-set-performance-data-file-name-options.md)|
|在 [啟動] 頁面上，如果您的程式碼方案中有多個 .exe 專案，請指定要啟動的應用程式。|- [如何：指定要啟動的二進位檔](../profiling/how-to-specify-the-binary-to-start.md)|
|在 [階層互動]  頁面上，將 ADO.NET 呼叫資料加入程式碼剖析執行。|- [收集階層互動資料](../profiling/collecting-tier-interaction-data.md)|
|在 [Windows 計數器]  頁面上，指定將加入程式碼剖析資料為標記的一或多個作業系統效能計數器。|- [如何：收集 Windows 計數器資料](../profiling/how-to-collect-windows-counter-data.md)|
|如果您的應用程式模組使用多個版本，請在 [ **Advanced** ] 頁面指定要進行分析的 .NET Framework 執行時間的版本。 預設會分析載入的第一個版本。|- [如何：指定 .NET Framework 執行時間](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
