---
title: "建立 SharePoint 工作流程方案 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
ms.assetid: fe79b99a-cb7c-4a14-8d9f-bce0c0805ba0
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 97283921205eaf70c77c054b269ee56f0e1adcd7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="creating-sharepoint-workflow-solutions"></a>建立 SharePoint 工作流程方案
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]提供的工具可協助您建立自訂工作流程，管理生命週期的文件和 SharePoint 網站的清單項目。 提供的項目包括設計工具、一組活動控制項，以及必要的組件參考。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]也包含**SharePoint 自訂精靈**協助建立及設定工作流程。  
  
 如需建立 SharePoint 專案中的必要條件清單[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，請參閱[開發 SharePoint 方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。 如需有關 SharePoint 的詳細資訊，請參閱[Microsoft SharePoint 產品與技術](http://go.microsoft.com/fwlink/?LinkId=178470)。  
  
## <a name="workflows-in-sharepoint"></a>在 SharePoint 中的工作流程  
 當您新增至 SharePoint 文件庫或清單的工作流程時，您強制執行商務程序，在文件庫或清單中的所有項目上。 工作流程會描述系統或使用者必須在每個項目，例如傳送要編輯，然後檢閱的項目執行的動作。 這些動作，稱為*活動*，是工作流程的建置組塊。  
  
 您可以建立 SharePoint 工作流程中的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]並將其部署至 SharePoint 網站。 工作流程部署至 SharePoint 之後，您關聯與程式庫或清單。 它可以再自動啟動，處理程序，或以手動方式，由的使用者。 如需工作流程作業的詳細資訊，請參閱[管理處理程序中使用工作流程](http://go.microsoft.com/fwlink/?LinkId=79757)。  
  
## <a name="creating-custom-sharepoint-workflows"></a>建立自訂 SharePoint 工作流程  
 兩個 SharePoint 工作流程專案可供您在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]:**循序工作流程**和**狀態機器工作流程**。  
  
 A*循序工作流程*代表一系列的步驟。 這些步驟會執行一個接著一個直到最後一個活動完成為止。 循序工作流程都在其執行嚴格的順序。 因為它們可以接收外部事件，並包括平行邏輯流程，所以可能會執行的確切順序。 下圖顯示循序工作流程的範例。  
  
 ![循序工作流程](../sharepoint/media/sp-sequential.png "循序工作流程")  
  
 A*狀態機器工作流程*代表一組狀態、 轉換和動作。 以非同步方式執行的狀態機器工作流程中的步驟。 這表示它們並不一定會執行，但改為所觸發的動作和狀態。 開始狀態，則會指派一個狀態，然後以事件為基礎，轉換為對另一個狀態。 狀態機器可以有最終狀態，決定工作流程的結尾。 下圖顯示狀態機器工作流程的範例。  
  
 ![狀態機器工作流程](../sharepoint/media/sp-state.png "狀態機器工作流程")  
  
 如需工作流程類型的詳細資訊，請參閱[工作流程類型](http://go.microsoft.com/fwlink/?LinkId=178995)。  
  
### <a name="using-the-wizard"></a>使用精靈  
 當您建立 SharePoint 工作流程專案中的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，您先指定在其設定**SharePoint 自訂精靈**。 精靈會建立一個專案中的使用這些設定**方案總管 中**。 此專案包含程式碼檔，用來部署工作流程的數個檔案，以及建立自訂 SharePoint 工作流程所需的組件參考。  
  
 建立工作流程之後，您可以修改其屬性，在 [屬性] 視窗中。 雖然大部分的工作流程屬性可以直接在 [屬性] 視窗中變更，但是有些會需要您按一下省略符號按鈕 (![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")) 至變更其值。 這個按鈕會重新啟動**SharePoint 自訂精靈**。 屬性值變更，請選擇後**完成**按鈕來完成這些程序。  
  
> [!NOTE]  
>  **工作流程類型**屬性是唯讀的而且無法變更。 如果您想要變更工作流程類型時，您必須建立另一個工作流程。  
  
## <a name="designing-a-sharepoint-workflow"></a>設計 SharePoint 工作流程  
 您定義商務程序中的所有步驟之後，請使用[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]設計 SharePoint 工作流程的工作流程設計工具。 若要開啟設計工具，請按兩下 Workflow1.cs 或 Workflow1.vb 中的**方案總管] 中**，或開啟任何這些檔案的捷徑功能表，然後選擇 [**開啟**。  
  
### <a name="activities"></a>活動  
 若要設計工作流程，將活動從新增**工具箱**至*工作流程排程*設計工具上。 工作流程排程包含中的順序，應該執行的活動序列。  
  
 有兩種類型的活動：  
  
-   *簡單的活動*執行單一單位的工作，例如 「 1 天延遲 」 或 「 啟動 Web 服務 」。  
  
-   *複合活動*包含其他活動; 例如，條件式活動可能包含兩個分支。  
  
 這兩種活動位於**工具箱**。  
  
 活動可以具有屬性、 方法和事件。 使用**屬性**視窗設定活動內容。  
  
 您也可以建立自訂活動。 如需詳細資訊，請參閱[逐步解說： 建立自訂站台工作流程活動](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)。  
  
 活動會組織中的下列索引標籤**工具箱**:  
  
-   **SharePoint 工作流程**  
  
-   **Windows Workflow v3.0**  
  
-   **Windows Workflow v3.5**  
  
 並非所有的核心工作流程活動支援 SharePoint。 如需詳細資訊，請參閱[工作流程活動的 Windows SharePoint Services 概觀](http://go.microsoft.com/fwlink/?LinkID=156094)。  
  
#### <a name="sharepoint-workflow-activities"></a>SharePoint 工作流程活動  
 **SharePoint 工作流程** 索引標籤包含專用的活動，以用於[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]。 這些活動會簡化，並簡化開發的文件的生命週期工作流程。 如需中所列的活動**SharePoint 工作流程**索引標籤上，請參閱[工作流程活動的 Windows SharePoint Services 概觀](http://go.microsoft.com/fwlink/?LinkID=156094)。  
  
#### <a name="windows-workflow-activities"></a>Windows 工作流程活動  
 **Windows 工作流程** 索引標籤包含活動所提供的[!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)]。 您可以使用這些活動建立工作流程排程的任何一種 Windows 工作流程應用程式。  
  
 如需中所列的活動**Windows 工作流程**索引標籤上，請參閱[Windows Workflow Foundation 活動](http://go.microsoft.com/fwlink/?LinkID=156096)。 如需有關 Windows Workflow Foundation 的詳細資訊，請參閱[Windows Workflow Foundation 概觀](http://go.microsoft.com/fwlink/?LinkID=128632)。  
  
### <a name="working-with-activities-in-the-designer"></a>使用設計工具中的活動  
 您的工作流程排程，可以包含 Windows 工作流程活動和 SharePoint 工作流程活動的組合。  
  
 在設計工具會顯示視覺提示，可協助您定位和正確設定活動。 當您將活動拖曳或複製到工作流程排程時，設計工具會顯示綠色的加號 (+) 圖示，表示工作流程中該活動的有效位置。 您無法位置它不是有效的位置來放置活動。 例如，您無法定位傳送活動的第一個活動為接聽活動分支中。 如需詳細資訊，請參閱[SharePoint Designer 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=178476)。  
  
## <a name="collecting-information-during-the-workflow"></a>在工作流程期間收集的資訊  
 您可能想要從使用者收集資訊在預先定義的工作流程中的時間。 您可以使用表單或項目屬性來收集資訊。  
  
### <a name="forms"></a>表單  
 表單就像是對話方塊中，其包含的問題並且提供方法讓使用者回答。  
  
 有四種類型的可用工作流程中的表單：  
  
-   關聯  
  
-   初始化  
  
-   修改  
  
-   工作  
  
 其中，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]包含關聯與初始化表單的項目範本。 舉例來說，*關聯表單*是可讓系統管理員安裝工作流程的其中一個輸入參數與工作流程，例如費用工作流程的消費限制。 舉例來說，*初始表單*是指可讓費用工作流程的使用者輸入到工作流程所花的數量。 如需這些表單類型的詳細資訊，請參閱[SharePoint 專案與專案項目範本](../sharepoint/sharepoint-project-and-project-item-templates.md)。  
  
### <a name="item-properties"></a>項目屬性  
 您也可以使用 SharePoint 文件庫或清單中項目的屬性，從使用者收集資訊。 主要的程式碼檔案 （Workflow1.cs 或 Workflow1.vb） 會宣告名為 Microsoft.SharePoint.Workflow.SPWorkflowActivationProperties.WorkflowProperties 類別的執行個體`workflowProperties`。 使用`workflowProperties`物件來存取文件庫或清單中的程式碼的屬性。 如需範例，請參閱[逐步解說： 建立及偵錯 SharePoint 工作流程方案](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)。  
  
## <a name="debugging-a-sharepoint-workflow-template"></a>偵錯 SharePoint 工作流程範本  
 您可以偵錯 SharePoint 工作流程專案相同當您偵錯其他[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Web 型的專案。 當您啟動[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]偵錯工具，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]會使用您在中指定的設定**SharePoint 自訂精靈**開啟適當的 SharePoint 網站，並自動建立關聯的工作流程範本使用適當的程式庫或清單中。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]也會將附加[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]偵錯工具，[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]名為 w3wp.exe 處理序。  
  
 若要測試工作流程，您必須手動啟動它。 如需詳細資訊，請參閱 < > 一節 < 偵錯工作流程中[偵錯 SharePoint 方案](../sharepoint/debugging-sharepoint-solutions.md)。 如需有關[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Web 應用程式偵錯，請參閱[偵錯 Web 應用程式和指令碼](/visualstudio/debugger/debugging-web-applications-and-script)。  
  
## <a name="deploying-a-sharepoint-workflow-template"></a>部署 SharePoint 工作流程範本  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]就像其他部署的 SharePoint 工作流程專案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 專案。 如需詳細資訊，請參閱[封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)。  
  
## <a name="importing-globally-reusable-workflows"></a>匯入可全域重複使用的工作流程  
 除了建立站台特有的可重複使用工作流程，SharePoint Designer 可讓您建立*可全域重複使用的工作流程*，這是可供任何 SharePoint 網站的工作流程。 中的匯入可重複使用工作流程專案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]目前不會匯入可全域重複使用的工作流程。 不過，您可以使用 SharePoint Designer 可全域重複使用的工作流程轉換成可重複使用工作流程，，或匯入工作流程作為未轉換的宣告式工作流程。 如需詳細資訊，請參閱[匯入現有的 SharePoint 網站中的項目](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[逐步解說：建立並偵錯 SharePoint 工作流程方案](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|將引導您逐步完成建立及偵錯簡單[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]工作流程。|  
|[逐步解說：使用關聯與初始化表單建立工作流程](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|逐步引導您建立更完整[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]關聯與初始化表單的工作流程完成。|  
|[逐步解說：將應用程式頁面新增到工作流程](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|在主題上建置[逐步解說： 建立工作流程關聯與初始化表單與](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)加入報表資料輸入到工作流程的其他.aspx 應用程式頁面。|  
|[逐步解說：建立自訂網站工作流程活動](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|示範如何執行兩項重要工作： 建立站台層級的工作流程，並建立自訂工作流程活動。|  
|[逐步解說：將 SharePoint Designer 可重複使用的工作流程匯入 Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|示範如何匯入 SharePoint Designer 2010 中建立的可重複使用宣告式工作流程[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 專案。|  
  
## <a name="see-also"></a>請參閱  
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)   
 [建置和偵錯 SharePoint 方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)  
  
  