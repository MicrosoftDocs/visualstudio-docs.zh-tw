---
title: 建立 SharePoint 工作流程方案 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VSTO.NewSharePointWorkflowWizard.Page3
- VS.SharePointTools.Workflow.WorkflowName
- VSTO.NewSharePointWorkflowWizard.Page2
- VSTO.NewSharePointWorkflowWizard.Page1
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2c787009577735213437140513ec095f81c3f43b
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015289"
---
# <a name="create-sharepoint-workflow-solutions"></a>建立 SharePoint 工作流程方案

[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]提供的工具可協助您建立自訂工作流程，以管理 SharePoint 網站中檔和清單專案的生命週期。 提供的項目包括設計工具、一組活動控制項，以及必要的組件參考。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]也包含**SharePoint 自訂嚮導**，以協助建立及設定工作流程。

如需有關 SharePoint 的詳細資訊，請參閱[Microsoft Sharepoint 產品和技術](/sharepoint/dev/)。

## <a name="workflows-in-sharepoint"></a>SharePoint 中的工作流程
 當您將工作流程加入至 SharePoint 文件庫或清單時，您會在文件庫或清單中的所有專案上強制執行商務程式。 工作流程會描述系統或使用者必須在每個專案上執行的動作，例如傳送要編輯的專案，然後再進行檢查。 這些動作（稱為「*活動*」）是工作流程的建立區塊。

 您可以在中建立 SharePoint 工作流程 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，並將其部署至 Sharepoint 網站。 將工作流程部署到 SharePoint 之後，您可以將它與程式庫或清單產生關聯。 然後，使用者可以自動啟動它、處理常式或手動啟動。 如需工作流程作業的詳細資訊，請參閱[使用 Visual Studio 開發 SharePoint 工作流程](/sharepoint/dev/general-development/develop-sharepoint-workflows-using-visual-studio)。

## <a name="create-custom-sharepoint-workflows"></a>建立自訂 SharePoint 工作流程
 您可以在中使用兩個 SharePoint 工作流程專案 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ：**順序工作流程**和**狀態機器工作流程**。

 *連續工作流程*代表一系列的步驟。 這些步驟會逐一執行，直到最後一個活動完成為止。 連續工作流程一律會在其執行中嚴格地順序。 因為它們可以接收外來事件並包含平行邏輯流程，所以執行的確切順序可能會有所不同。 下圖顯示順序工作流程的範例。

 ![循序性工作流程](../sharepoint/media/sp-sequential.png "循序性工作流程")

 *狀態機器工作流程*代表一組狀態、轉換和動作。 狀態機器工作流程中的步驟會以非同步方式執行。 這表示它們不一定會在另一個之後執行，而是由動作和狀態觸發。 其中一個狀態會指派為開始狀態，然後根據事件，轉換為另一個狀態。 狀態機器可以具有判斷工作流程結束的最終狀態。 下圖顯示狀態機器工作流程的範例。

 ![狀態機器工作流程](../sharepoint/media/sp-state.png "狀態機器工作流程")

 如需工作流程類型的詳細資訊，請參閱[工作流程類型](/previous-versions/office/developer/sharepoint-2010/ms468447(v=office.14))。

### <a name="use-the-wizard"></a>使用 wizard
 當您在中建立 SharePoint 工作流程專案時 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，您必須先在**Sharepoint 自訂嚮導**中指定其設定。 Wizard 會使用這些設定，在**方案總管**中建立專案。 此專案包含程式碼檔案、用來部署工作流程的數個檔案，以及建立自訂 SharePoint 工作流程所需元件的參考。

 建立工作流程之後，您可以在屬性視窗中修改其屬性。 雖然大部分的工作流程屬性可以直接在屬性視窗中變更，但有些則需要您按一下省略號按鈕（![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")）來變更其值。 此按鈕會重新開機**SharePoint 自訂嚮導**。 在您進行屬性值變更之後，請選擇 [**完成]** 按鈕來完成這些作業。

> [!NOTE]
> [**工作流程類型**] 屬性是唯讀的，無法變更。 如果您想要變更工作流程類型，您必須建立另一個工作流程。

## <a name="design-a-sharepoint-workflow"></a>設計 SharePoint 工作流程
 在您定義商務程式中的所有步驟之後，請使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 工作流程設計工具來設計 SharePoint 工作流程。 若要開啟設計工具，請按兩下**方案總管**中的 [Workflow1.cs] 或 [workflow1.xaml]，或開啟其中任一檔案的快捷方式功能表，然後選擇 [**開啟**]。

### <a name="activities"></a>活動
 若要設計工作流程，請從 [**工具箱**] 將活動加入至設計工具上的*工作流程排程*。 工作流程排程包含活動順序，其順序應應執行。

 活動可分為兩種：

- *簡單的活動*會執行單一工作單位，例如「一天的延遲時間」或 [啟動 Web 服務]。

- *複合活動*包含其他活動;例如，條件式活動可能會包含兩個分支。

  這兩種類型的活動都可以在 [**工具箱**] 中使用。

  活動可以有屬性、方法和事件。 使用 [**屬性**] 視窗來設定活動的屬性。

  您也可以建立自訂活動。 如需詳細資訊，請參閱[逐步解說：建立自訂網站工作流程活動](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)。

  活動會組織于 [**工具箱**] 的下列索引標籤中：

- **SharePoint 工作流程**

- **Windows Workflow v3。0**

- **Windows Workflow v 3。5**

  SharePoint 不支援所有核心工作流程活動。 如需詳細資訊，請參閱[Windows SharePoint Services 的工作流程活動總覽](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14))。

#### <a name="sharepoint-workflow-activities"></a>SharePoint 工作流程活動
 [ **SharePoint 工作流程**] 索引標籤包含在中使用的特定活動 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 。 這些活動會簡化和簡化檔生命週期工作流程的開發。 如需 [ **Sharepoint 工作流程**] 索引標籤中所列活動的詳細資訊，請參閱[Windows Sharepoint Services 的工作流程活動總覽](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14))。

#### <a name="windows-workflow-activities"></a>Windows 工作流程活動
 [ **Windows 工作流程**] 索引標籤包含所提供的活動 [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)] 。 您可以使用這些活動來建立任何一種 Windows workflow 應用程式的工作流程排程。

 如需 [ **Windows 工作流程**] 索引標籤中所列活動的詳細資訊，請參閱[Windows Workflow Foundation 活動](/previous-versions/dotnet/netframework-3.5/ms733615(v=vs.90))。 如需 Windows Workflow Foundation 的詳細資訊，請參閱[Windows Workflow Foundation 總覽](/previous-versions/dotnet/netframework-3.5/ms734631(v=vs.90))。

### <a name="work-with-activities-in-the-designer"></a>使用設計工具中的活動
 您的工作流程排程可以包含 Windows 工作流程活動和 SharePoint 工作流程活動的組合。

 設計工具會顯示視覺提示，協助您正確地定位及設定活動。 當您將活動拖曳或複製到工作流程排程時，設計工具會顯示綠色的加號 (+) 圖示，表示工作流程中該活動的有效位置。 您不能將活動放在其不正確位置。 例如，您無法將 Send 活動置於「接聽活動」分支中的第一個活動。 如需詳細資訊，請參閱[SharePoint Designer 開發人員中心](https://developer.microsoft.com/office/docs)。

## <a name="collect-information-during-the-workflow"></a>在工作流程期間收集資訊
 在工作流程中，您可能會想要在預先定義的時間收集使用者的資訊。 您可以使用表單或專案屬性來收集資訊。

### <a name="forms"></a>表單
 表單就像是包含問題的對話方塊，可讓使用者提供解答。

 有四種類型的表單可以在工作流程中使用：

- 關聯

- 提出

- 修改

- Task

  其中包括 [ [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 關聯] 和 [起始] 表單的專案範本。 *關聯表單*的範例之一，是讓系統管理員安裝工作流程輸入與工作流程相關的參數，例如支出工作流程的消費限制。 *起始表單*的範例之一，就是讓「支出工作流程」的使用者輸入他們在工作流程中花費的金額。 如需這些表單類型的詳細資訊，請參閱[SharePoint 專案和專案專案範本](../sharepoint/sharepoint-project-and-project-item-templates.md)。

### <a name="item-properties"></a>專案屬性
 您也可以使用 SharePoint 文件庫或清單中專案的屬性，從使用者收集資訊。 主要的程式碼檔案（Workflow1.cs 或 Workflow1.xaml）會宣告名為的 SPWorkflowActivationProperties WorkflowProperties 類別實例 `workflowProperties` 。 使用 `workflowProperties` 物件來存取程式碼中程式庫或清單的屬性。 如需範例，請參閱[逐步解說：建立和執行 SharePoint 工作流程方案的調試](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)程式。

## <a name="debug-a-sharepoint-workflow-template"></a>Debug SharePoint 工作流程範本
 您可以使用與調試其他 Web 專案相同的方式，來進行 SharePoint 工作流程專案的 debug [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。 當您啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 偵錯工具時， [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會使用您在**SharePoint 自訂嚮導**中指定的設定來開啟適當的 SharePoint 網站，並自動將工作流程範本與適當的程式庫或清單產生關聯。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]也會將 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 偵錯工具附加至 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 名為*w3wp.exe*的進程。

 若要測試工作流程，您必須手動啟動它。 如需詳細資訊，請參閱[偵錯工具 SharePoint 方案](../sharepoint/debugging-sharepoint-solutions.md)中的「偵錯工具工作流程」一節。 如需 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] web 應用程式的詳細資訊，請參閱[Debug web applications 和 script](../debugger/how-to-enable-debugging-for-aspnet-applications.md)。

## <a name="deploy-a-sharepoint-workflow-template"></a>部署 SharePoint 工作流程範本
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 工作流程專案的部署方式就像其他 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sharepoint 專案一樣。 如需詳細資訊，請參閱[封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)。

## <a name="import-globally-reusable-workflows"></a>匯入全域可重複使用的工作流程
 除了建立網站特定可重複使用的工作流程，SharePoint Designer 可讓您建立*全域可重複使用的工作*流程，這是可供任何 SharePoint 網站使用的工作流程。 中的 [匯入可重複使用的工作流程] 專案 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 目前不會匯入可全域重複使用 不過，您可以使用 SharePoint Designer 將全域可重複使用的工作流程轉換成可重複使用的工作流程，或將工作流程匯入為未轉換的宣告式工作流程。 如需詳細資訊，請參閱[從現有的 SharePoint 網站匯入專案](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)。

## <a name="related-topics"></a>相關主題

|Title|描述|
|-----------|-----------------|
|[逐步解說：建立和調試 SharePoint 工作流程方案](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|引導您逐步建立和調試簡單的 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 工作流程。|
|[逐步解說：使用關聯與初始表單建立工作流程](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|引導您 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 使用關聯與初始表單，逐步建立更完整的工作流程。|
|[逐步解說：將應用程式頁面新增至工作流程](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|建置於逐步解說[：使用關聯與初始表單建立工作流程一](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)節中，方法是加入額外的 *.aspx*應用程式頁面，以報告輸入至工作流程的資料。|
|[逐步解說：建立自訂網站工作流程活動](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|示範如何執行兩個主要工作：建立網站層級的工作流程，以及建立自訂工作流程活動。|
|[逐步解說：將 SharePoint Designer 可重複使用的工作流程匯入 Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|示範如何將 SharePoint Designer 2010 中建立的可重複使用的宣告式工作流程匯入至 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sharepoint 專案。|

## <a name="see-also"></a>另請參閱

- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
- [建置和偵錯 SharePoint 方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)