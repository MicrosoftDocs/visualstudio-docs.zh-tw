---
title: 建立 Workflow Foundation 專案
ms.date: 06/25/2018
ms.topic: conceptual
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f793e6ff468bdec6df499c5e5eb6b8524e9e4d5a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650567"
---
# <a name="workflow-project-templates"></a>工作流程專案範本

您可以使用 Visual Studio 專案範本，建立工作流程、Windows Communication Foundation （WCF）工作流程服務、自訂活動和自訂活動設計工具。 本文說明如何使用 Visual Studio 中提供的專案範本來建立程式庫和應用程式。

## <a name="create-a-workflow-project"></a>建立工作流程專案

Visual Studio 提供四種不同的工作流程專案範本：

- 工作流程主控台應用程式

- WCF 工作流程服務應用程式

- 活動程式庫

- 活動設計工具程式庫

若要存取這些範本，請先安裝 Visual Studio 的**Windows Workflow Foundation**元件。 如需詳細指示，請參閱[Install Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation)。

1. 安裝**Windows Workflow Foundation**元件之後，**請選取 [** 檔案  > **新增** > **專案**]。

1. 搜尋並選取工作流程專案範本，例如，**工作流程主控台應用程式**範本。

1. 繼續建立專案。

   > [!NOTE]
   > 如果您想要將新的專案加入至現有的方案，請在 Visual Studio 中開啟該方案，以滑鼠右鍵按一下**方案總管**中的方案，**然後選取 [新增  > ** **新專案**]。

## <a name="workflow-console-app"></a>工作流程主控台應用程式

如果您選擇 [**工作流程主控台應用程式**] 範本，Visual Studio 會在 XAML 中建立工作流程定義。 工作流程設計工具會開啟並顯示您所建立之工作流程的畫布。 若要撰寫工作流程，請將活動或其他工作流程專案從 [**工具箱**] 拖曳至設計介面。

## <a name="wcf-workflow-service-app"></a>WCF 工作流程服務應用程式

如果您選擇 [ **WCF 工作流程服務應用程式**] 範本，Visual Studio 會將服務定義建立為 XAML。 工作流程設計工具會在設計檢視中開啟，其中包含一組 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 活動的 <xref:System.Activities.Statements.Sequence> 活動。

## <a name="activity-library"></a>活動程式庫

如果您選擇 [**活動程式庫**] 範本，Visual Studio 會在 XAML 中建立活動定義。 工作流程設計工具會開啟並顯示自訂活動的畫布。 將活動從 [**工具箱**] 拖曳至設計介面，以將它包含在您的自訂活動中。

> [!NOTE]
> 您在自訂活動的主體中只允許一個子活動。 不過，該子活動可以是複合活動，例如 <xref:System.Activities.Statements.Sequence> 活動或 <xref:System.Activities.Statements.Flowchart> 活動。

## <a name="activity-designer-library"></a>活動設計工具程式庫

如果您選擇 [**活動設計**工具程式庫] 範本，Visual Studio 會在 XAML 中建立活動設計工具定義，並在程式碼後置執行檔案。 工作流程設計工具會開啟並顯示活動設計工具的畫布。 將 Windows Presentation Foundation （WPF）控制項從 [工具箱] 拖曳至設計介面，以便在您的自訂活動設計**工具**中使用它們。

如需如何執行自訂活動設計工具的範例，請參閱[如何：建立自訂活動設計](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer)工具。

> [!NOTE]
> 自訂活動設計工具可用於自訂活動和預設 .NET 活動。

## <a name="see-also"></a>請參閱

- [使用工作流程設計工具](developing-applications-with-the-workflow-designer.md)
- [設計工作流程（.NET Framework）](/dotnet/framework/windows-workflow-foundation/designing-workflows)