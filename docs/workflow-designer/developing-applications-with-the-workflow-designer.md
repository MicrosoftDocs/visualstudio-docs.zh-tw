---
title: 使用工作流程設計工具開發應用程式 |Microsoft 文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DefaultWorkflowDesigner
- DefaultWorkflowDesigner.UI
helpviewer_keywords:
- Visual Studio 2010 Workflow Designer [WFD], overview
- Workflow Designer [WFD]
- Visual Studio 2010 Workflow Designer [WFD]
- Workflow Designer [WFD], overview
ms.assetid: 4cd062b1-b496-4668-bbc1-ee85545e066d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9c48e7b43b23e7bfe8887f437cc17e6db077c0e4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="developing-applications-with-the-workflow-designer"></a>使用工作流程設計工具開發應用程式

Windows 工作流程設計工具是視覺化設計工具和偵錯工具的圖形建構與偵錯[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]中的應用程式[!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)]裝載在[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]開發環境。 它可讓您使用範本與活動設計工具，來撰寫複合工作流程應用程式、活動程式庫或 [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] 服務。 如需工作流程的詳細資訊，請參閱[Windows Workflow Foundation &#91;.NET Framework 4&#93;](http://msdn.microsoft.com/Library/9a23ea6b-d600-483e-89cd-8889cfec5f66)。

 以下是幾個使這個新版 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 與舊版 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 不同的新設計功能：

-   使用 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 建立的 [!INCLUDE[avalon1](../workflow-designer/includes/avalon1_md.md)]。 這會提升活動設計工具的體驗，並改善大型且複雜之工作流程的效能。

-   現在會使用 [!INCLUDE[avalon2](../workflow-designer/includes/avalon2_md.md)] 來設計自訂活動，以簡化為建立活動設計工具而使用 XAML 和程式設計模型的方式。

-   流程圖活動已實作，因此可使用相似的流程圖模型樣式來視覺化程式的流程。

-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 有新的變數設計工具，可讓您宣告工作流程內的變數與設定其範圍，以及將變數繫結至活動。

-   在 [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] 中，[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 會提供在 [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] 工作流程內撰寫 Visual Basic 運算式時的完整 IntelliSense 功能。

-   現在，偵錯體驗已延伸到 XAML，您可在 XAML 工作流程定義中設定中斷點，以及在執行階段步入 XAML 程式碼，提供與使用 Managed 程式碼相似的經驗。

-   相較於舊版，重新裝載 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 之外的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 已大幅簡化，現在只需要幾行程式碼即可完成。

-   新<xref:System.Activities.Statements.Flowchart>活動及其[流程圖](../workflow-designer/flowchart-activity-designer.md)可讓您視覺化程式的流程使用熟悉的流程圖模型樣式。

-   傳訊活動已有所加強，可讓您撰寫完全宣告式 (無程式碼) 的 [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] 服務。

-   **加入服務參考...**功能可讓您產生的活動會自動存取 Web 服務。