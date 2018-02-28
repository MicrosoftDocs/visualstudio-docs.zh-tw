---
title: "逐步解說： 將 SharePoint Designer 可重複使用工作流程匯入 Visual Studio |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.WSPImport.ImportWF
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing reusable workflows
- reusable workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 05428f2e702643b88415663249e9f29a9f7d46bc
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio"></a>逐步解說：將 SharePoint Designer 可重複使用的工作流程匯入 Visual Studio
  本逐步解說示範如何匯入 SharePoint Designer 2010 中建立的可重複使用工作流程[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 工作流程專案。  
  
 在 SharePoint Designer 中建立的工作流程或*宣告式工作流程*，組成[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]陳述式，而非程式碼。 SharePoint Designer 2010 導入了*可重複使用的工作流程*，這是可攜式、 宣告式工作流程，可供 SharePoint 網站中不同的清單。  
  
 在中建立的工作流程[!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]，例如循序和狀態機器工作流程，稱為*程式碼工作流程*。 程式碼工作流程是由 XML 檔案中，使用者可以自訂工作流程的行為的程式碼模組所組成。  
  
 Visual Studio 可讓您匯入 SharePoint Designer 2010 中建立之可重複使用的工作流程，並將它們轉換成程式碼工作流程，以便在 SharePoint 網站中使用。  
  
 本逐步解說將示範下列工作：  
  
-   在 SharePoint Designer 中建立簡單且可重複使用工作流程。  
  
-   .Wsp 檔案，並置於 SharePoint 匯出 SharePoint Designer 可重複使用工作流程。  
  
-   匯入.wsp 檔案貼入[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]使用匯入可重複使用工作流程專案。  
  
-   加入程式碼來變更工作流程。  
  
-   在 SharePoint 網站中使用匯入工作流程。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的版本[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]和 SharePoint。 如需詳細資訊，請參閱[開發 SharePoint 方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
-   Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010。  
  
## <a name="create-target-sharepoint-subsites"></a>建立目標 SharePoint 子網站  
 建立兩個新的 SharePoint 子網站的第一次： 一裝載從另一個則是裝載已轉換的工作流程的 SharePoint Designer 可重複使用的工作流程。  
  
#### <a name="to-create-sharepoint-subsites"></a>建立 SharePoint 網站  
  
1.  在 SharePoint Designer 2010 中，功能表列上選擇 **檔案**，**新增空白網站**。  
  
2.  在**新增空白網站**對話方塊中，瀏覽至 SharePoint 網站，您要建立工作流程，或使用 http:// 的值*系統名稱*/，然後選擇 **確定**按鈕。  
  
     [首頁] 頁面隨即出現。  
  
3.  在**子網站**區段中，選擇**新增** 按鈕。  
  
4.  在**新增**對話方塊方塊中，選擇**SharePoint 範本**從左窗格中的清單，然後選擇 **小組網站**從右窗格中的清單。  
  
5.  在**指定網站的位置**方塊中，取代這個字**子網站**URL 中**SPD1**，然後選擇 [ **[確定]** ] 按鈕。  
  
     這會開啟 SharePoint 設計工具中，新的子網站。 關閉 SharePoint Designer 的這個執行個體，並回到第一個執行個體 （最上層站台）。  
  
6.  重複步驟 3-5 建立第二個的子網站，此時取代單字**子網站**中[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]與**SPD2**。  
  
## <a name="create-a-sharepoint-designer-reusable-workflow"></a>建立 SharePoint Designer 可重複使用工作流程  
 因為 SharePoint 不包含任何可重複使用的工作流程，您可以使用此範例中，您會建立一個。 在這個簡單的工作流程，當使用者有特定的標題，工作清單 中輸入新工作的工作指派給該使用者。  
  
#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>若要建立 SharePoint Designer 可重複使用工作流程  
  
1.  在**子網站**區段中，選擇**SPD1**網站進行修改。  
  
2.  在功能區中，選擇 [**可重複使用工作流程**] 按鈕。  
  
     建立可重複使用工作流程精靈 隨即出現。  
  
3.  在**名稱**方塊中，輸入**SPD Task Workflow**。  
  
4.  在**內容類型**清單中，選擇**工作**，然後選擇 [**確定**] 按鈕。  
  
     工作流程會在 SharePoint Designer 的工作流程設計工具中開啟。  
  
5.  在工作流程設計工具中，選擇 步驟 1，然後，在功能區中，選擇 **條件** 按鈕。  
  
6.  在條件清單中，選擇 **如果目前的項目欄位等於值**。  
  
     這個步驟會加入名為條件**如果欄位等於值**。  
  
7.  在**如果欄位等於值**條件中，選擇**欄位**連結。  
  
8.  在值的清單中選擇**標題**。  
  
9. 在**如果欄位等於值**條件中，選擇**值**連結。  
  
10. 在方塊中，輸入**新工作**。  
  
     條件陳述式現在會讀取**如果目前項目： 標題等於新工作**。  
  
11. 選擇條件陳述式下的那一行，然後在功能區中，選擇**動作** 按鈕。  
  
12. 在動作清單中，選擇 **目前的項目中設定欄位**。  
  
13. 在**集欄位值**動作中，選擇**欄位**連結，，然後在清單中，選擇**指派給**。  
  
14. 在**集欄位值**動作，選擇**值**連結，，然後在現有的使用者和群組的清單中，選擇**建立之項目的使用者**。  
  
15. 選擇**新增**按鈕，然後再選擇**確定** 按鈕。  
  
     Action 陳述式現在會讀取**設定指派給到目前項目： CreatedBy**。  
  
## <a name="save-and-deploy-the-reusable-workflow"></a>儲存和部署可重複使用的工作流程  
 因為[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]可以匯入只能.wsp 檔案中，您必須將可重複使用的工作流程儲存為.wsp 檔案，並將它匯入之前將它部署到 SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
> [!IMPORTANT]  
>  如果您收到執行階段錯誤，執行下列程序，您必須有權存取 SharePoint 網站的系統上執行程序。  
  
#### <a name="to-save-and-deploy-the-reusable-workflow"></a>若要儲存和部署可重複使用的工作流程  
  
1.  SharePoint Designer 頂端選擇**儲存**按鈕儲存您的進度，然後選擇 **發行**按鈕，將部署工作流程**SPD1** SharePoint 網站.  
  
2.  在瀏覽窗格中，選擇 **工作流程**物件。  
  
3.  在下**可重複使用工作流程**，選擇**SPD Task Workflow**。  
  
4.  在功能區中，選擇 **另存為範本**按鈕可以將工作流程儲存為.wsp 檔案。  
  
5.  開啟**SPD1**瀏覽器在 SharePoint 中檢視.wsp 檔案中的 SharePoint 網站。  
  
6.  在 快速啟動 列上選擇 **文件庫**連結。  
  
7.  在**文件庫**區段中，選擇**網站資產**連結。  
  
     **SPD Task Workflow**檔案與其他網站資產的清單。  
  
8.  在檔案清單中，選擇該檔案的名稱  
  
9. 在**檔案下載**對話方塊方塊中，選擇**儲存**按鈕以儲存您的本機系統上的.wsp 檔案。  
  
## <a name="import-the-wsp-file-into-visual-studio"></a>.Wsp 檔案匯入 Visual Studio  
 .wsp 檔案匯入[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]使用匯入可重複使用工作流程專案。 這個專案將可重複使用、 宣告式工作流程內的工作流程轉換程式碼工作流程。 工作流程轉換之後，您會使用程式碼來修改其行為。  
  
#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>要從.wsp 檔案匯入工作流程，並加以修改  
  
1.  在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，在功能表列上選擇 **檔案**，**新增**，**專案**。  
  
2.  在**新專案**對話方塊方塊中，展開  **SharePoint**節點之下**Visual C#**或**Visual Basic**，然後選擇  **2010年**節點。  
  
3.  在**範本** 窗格中，選擇**匯入可重複使用 SharePoint 2010 工作流程**範本，將保留做為專案的名稱**WorkflowImportProject1**，然後選擇 **確定** 按鈕。  
  
     SharePoint 自訂精靈隨即出現。  
  
4.  在**指定偵錯的網站和安全性層級**頁面上，輸入[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]您先前建立的第二個 SharePoint 子網站： http://*系統名稱*/SPD2。  
  
5.  在**此 SharePoint 方案的信任層級為何？**區段中，選擇**部署為伺服陣列方案**選項按鈕，然後再選擇**下一步** 按鈕。  
  
     如需有關沙箱化和伺服器陣列方案，請參閱[沙箱化方案考量](../sharepoint/sandboxed-solution-considerations.md)。  
  
6.  在**指定新專案來源**頁面上，瀏覽至先前儲存.wsp 檔案的位置在系統上，開啟檔案，然後選擇**下一步** 按鈕。  
  
    > [!NOTE]  
    >  選擇**完成**匯入.wsp 檔案中所有可用的項目 按鈕。  
  
     這會顯示一份可供匯入可重複使用工作流程。  
  
7.  在**選取要匯入項目**方塊中，選擇**SPD Task Workflow**工作流程，然後選擇 [**完成**] 按鈕。  
  
     匯入作業完成之後，專案名為**WorkflowImportProject1**會建立包含名為工作流程**SPD_Workflow_TestFT**。 在此資料夾是工作流程的定義檔 Elements.xml 和工作流程設計工具檔案 (.xoml)。 在設計工具包含兩個檔案： 規則 (.rules) 檔和程式碼後置檔案 （.cs 或.vb，專案的程式設計語言而定）。  
  
8.  在**方案總管 中**，刪除**其他匯入檔案**資料夾。  
  
9. 在 Elements.xml 檔案中，刪除 `InstantiationURL="_layouts/IniErkflIP.sspx"`。  
  
10. 在**方案總管] 中**，選擇**WorkflowImportProject1**，然後在功能表列上選擇 [**專案**，**設定為啟始專案**至設定**WorkflowImportProject1**為啟動項目。  
  
     這會在偵錯專案時，立即顯示清單。  
  
11. 因為**匯入的可重複使用 SharePoint 2010 工作流程**範本不會匯入匯入工作流程的關聯屬性值，您必須輸入它們。 若要這樣做：  
  
    1.  在**方案總管 中**，選擇**SPD_Workflow_TestFT**節點。  
  
    2.  選擇省略符號 (![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")) 按鈕旁的清單屬性，例如**目標清單**屬性。  
  
    3.  填寫 SharePoint 自訂精靈中的遺漏值，然後選擇 **完成** 按鈕。  
  
12. 選擇.xoml 檔案]，然後在功能表列上選擇 [**檢視**，**設計師**在工作流程設計工具中檢視匯入工作流程。  
  
13. 在**Windows Workflow v3.0**節點**工具箱**，執行下列步驟：  
  
    -   開啟快顯功能表**程式碼**活動，然後選擇 **複製**。 在工作流程設計工具中，開啟 在下一行的捷徑功能表**SequenceActivity1**活動，然後選擇 **貼上**。  
  
    -   拖曳**程式碼**活動從**工具箱**至工作流程設計工具中，並將它連接至下一行**SequenceActivity1**活動。  
  
     這將活動加入至名為工作流程設計工具**CodeActivity1**。 在這個活動中，您將加入公告清單中建立通知，當使用者開始工作流程的程式碼動作。  
  
14. 請執行下列其中一組步驟：  
  
    -   按兩下**CodeActivity1**產生的事件處理常式，並檢視程式碼。  
  
    -   在**屬性**視窗**CodeActivity1**，設定的值**ExecuteCode**屬性**codeActivity_ExecuteCode**。  
  
15. 現有的下方加入下列**使用**或**匯入**陳述式：  
  
     [!code-csharp[SP_SPDWFImport#1](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]  
  
16. 取代`codeActivity1_ExecuteCode`為下列：  
  
     [!code-csharp[SP_SPDWFImport#2](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]  
  
## <a name="deploy-the-project-and-associate-the-workflow"></a>部署專案及關聯工作流程  
 接下來，執行 WorkflowImportProject1 將它部署到 SharePoint 網站，然後使用 [工作] 清單，即可檢視和修改測試關聯工作流程轉換成工作流程。  
  
#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>若要部署專案及關聯工作流程  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中，選擇 F5 鍵執行並部署轉換後的工作流程專案。  
  
2.  在 快速啟動 列上選擇 **工作**連結可以顯示 工作 清單。  
  
3.  在**清單工具**索引標籤上，選擇**項目**按鈕，然後再選擇**新項目** 按鈕。  
  
     **工作-新項目**對話方塊隨即開啟。  
  
4.  在**標題**方塊中，輸入**新工作**，然後選擇 [**儲存**] 按鈕。  
  
5.  在**清單工具**索引標籤上，選擇**清單**按鈕，然後再選擇**清單設定** 按鈕。  
  
     **清單設定**頁面隨即出現。  
  
6.  在**權限與管理**區段中，選擇**工作流程設定**連結。  
  
     **工作流程設定**頁面隨即出現。  
  
7.  選擇**加入工作流程**連結。  
  
8.  在**工作流程**清單中，選擇**WorkflowImportProject1-SPD Workflow Test**。  
  
9. 在**名稱**方塊中，輸入**SPD Workflow Test**，然後選擇 [**確定**] 按鈕。  
  
10. 在 快速啟動列上，選擇 **工作**清單。  
  
11. 選擇箭號旁**新工作**，然後在清單中，選擇 **工作流程**。  
  
12. 在**啟動新的工作流程**區段中，選擇連結**SPD Workflow Test**，然後選擇 **啟動**按鈕，以初始化工作流程。  
  
    > [!NOTE]  
    >  或者，您可以自動-與相關聯的工作流程清單以執行工作流程設定精靈，並設定工作流程，以自動產生關聯。  
  
     請注意，兩個動作都是透過工作流程： 您的名稱會出現在工作的**指派給**資料行，則宣告會出現在**公告**清單。  
  
## <a name="see-also"></a>請參閱  
 [從現有的 SharePoint 網站匯入的項目](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)   
 [為 Web 組件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  