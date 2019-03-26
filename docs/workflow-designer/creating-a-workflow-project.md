---
title: 建立 Workflow Foundation 專案
ms.date: 06/25/2018
ms.topic: conceptual
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 15c02312d5c257f13b9c0394790bc8a2611d7972
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2019
ms.locfileid: "58414754"
---
# <a name="workflow-project-templates"></a>工作流程專案範本

您可以使用 Visual Studio 專案範本，來建立工作流程、 Windows Communication Foundation (WCF) 工作流程服務、 自訂活動和自訂活動設計工具。 本文說明如何使用 Visual Studio 中可用的專案範本建立程式庫和應用程式。

## <a name="create-a-workflow-project"></a>建立工作流程專案

Visual Studio 提供四個不同的工作流程專案範本：

- 工作流程主控台應用程式

- WCF 工作流程服務應用程式

- 活動程式庫

- 活動設計工具程式庫

若要存取這些範本，請先安裝**Windows Workflow Foundation** Visual Studio 的元件。 如需詳細指示，請參閱 <<c0> [ 安裝的 Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation)。

1. 安裝之後**Windows Workflow Foundation**元件，選取**檔案** > **新增** > **專案**.

1. 搜尋並選取工作流程專案範本，比方說，則**工作流程主控台應用程式**範本。

1. 若要建立專案，以繼續執行。

   > [!NOTE]
   > 如果您想要將新的專案新增至現有的方案，在 Visual Studio 中開啟該方案，以滑鼠右鍵按一下方案中的**方案總管**，然後選取**新增** > **新增專案**。

## <a name="workflow-console-app"></a>工作流程主控台應用程式

如果您選擇**工作流程主控台應用程式**範本，Visual Studio 會建立工作流程定義在 XAML 中。 工作流程設計工具會開啟並顯示您所建立的工作流程的畫布。 若要撰寫工作流程，拖曳活動或從其他工作流程項目**工具箱**至設計介面。

## <a name="wcf-workflow-service-app"></a>WCF 工作流程服務應用程式

如果您選擇**WCF 工作流程服務應用程式**範本，Visual Studio 會建立服務定義為 XAML。 工作流程設計工具會開啟至 [設計] 檢視與<xref:System.Activities.Statements.Sequence>活動，其中包含一組<xref:System.ServiceModel.Activities.Receive>和<xref:System.ServiceModel.Activities.SendReply>活動。

## <a name="activity-library"></a>活動程式庫

如果您選擇**活動程式庫**範本，Visual Studio 會建立活動定義在 XAML 中。 工作流程設計工具會開啟並顯示您的自訂活動的畫布。 活動拖曳**工具箱**至設計介面，以將它包含在您的自訂活動。

> [!NOTE]
> 您可以在您的自訂活動的主體中只有一個子活動。 不過，該子活動可以是複合活動，例如<xref:System.Activities.Statements.Sequence>活動或<xref:System.Activities.Statements.Flowchart>活動。

## <a name="activity-designer-library"></a>活動設計工具程式庫

如果您選擇**活動設計工具程式庫**範本，Visual Studio 會建立活動設計工具定義在 XAML 和程式碼後置實作檔案中。 工作流程設計工具隨即開啟，並顯示您的活動設計工具畫布。 將 Windows Presentation Foundation (WPF) 控制項從**工具箱**至設計介面，以在您的自訂活動設計工具中使用它們。

如需如何實作自訂活動設計工具的範例，請參閱[How to:建立自訂活動設計工具](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer)。

> [!NOTE]
> 可用於自訂活動設計工具，自訂活動和用於預設.NET Framework 的活動。

## <a name="see-also"></a>另請參閱

- [使用工作流程設計工具](developing-applications-with-the-workflow-designer.md)
- [設計工作流程 (.NET Framework)](/dotnet/framework/windows-workflow-foundation/designing-workflows)