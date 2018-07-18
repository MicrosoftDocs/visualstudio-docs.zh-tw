---
title: 使用工作流程設計工具開發應用程式
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
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
ms.openlocfilehash: ecc9e42146bfa7de259551ff1c90d27201db5725
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970121"
---
# <a name="developing-applications-with-the-workflow-designer"></a>使用工作流程設計工具開發應用程式

Windows 工作流程設計工具是視覺化設計工具和偵錯工具的圖形建構與偵錯在 Visual Studio 2010 開發環境中裝載的.NET Framework 4 中的 Windows Workflow Foundation (WF) 應用程式。 它可讓您撰寫複合工作流程應用程式、 活動程式庫或透過使用範本與活動設計工具的 Windows Communication Foundation (WCF) 服務。 如需工作流程的詳細資訊，請參閱[Windows Workflow Foundation &#91;.NET Framework 4&#93;](http://msdn.microsoft.com/Library/9a23ea6b-d600-483e-89cd-8889cfec5f66)。

 以下是幾個設定這個新版本的舊版工作流程設計工具以外的工作流程設計工具的新設計功能：

-   工作流程設計工具是使用 Windows Presentation Foundation (WPF) 所建立。 這會提升活動設計工具的體驗，並改善大型且複雜之工作流程的效能。

-   現在會使用 [!INCLUDE[avalon2](../workflow-designer/includes/avalon2_md.md)] 來設計自訂活動，以簡化為建立活動設計工具而使用 XAML 和程式設計模型的方式。

-   流程圖活動已實作，因此可使用相似的流程圖模型樣式來視覺化程式的流程。

-   工作流程設計工具有新變數設計工具，可讓您宣告和範圍，工作流程內的變數繫結至活動。

-   在 Visual Studio 2010 中，工作流程設計工具會提供完整的 IntelliSense 功能，撰寫.NET Framework 4 工作流程內的 Visual Basic 運算式時。

-   現在，偵錯體驗已延伸到 XAML，您可在 XAML 工作流程定義中設定中斷點，以及在執行階段步入 XAML 程式碼，提供與使用 Managed 程式碼相似的經驗。

-   重新裝載工作流程設計工具，Visual Studio 之外，已大幅簡化相較於舊版，現在只需要幾行程式碼。

-   新<xref:System.Activities.Statements.Flowchart>活動及其[流程圖](../workflow-designer/flowchart-activity-designer.md)可讓您視覺化程式的流程使用熟悉的流程圖模型樣式。

-   傳訊活動已有所加強，可讓您撰寫完全宣告式 （無程式碼） Windows Communication Foundation (WCF) 服務。

-   **加入服務參考...** 功能可讓您產生的活動會自動存取 Web 服務。