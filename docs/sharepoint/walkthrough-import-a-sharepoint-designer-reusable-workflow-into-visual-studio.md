---
title: 逐步解說：SharePoint Designer 可重複使用工作流程匯入 Visual Studio |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.WSPImport.ImportWF
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing reusable workflows
- reusable workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c92a1023f5099c6a6d92df825aebebf35dd678dd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53821342"
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio"></a>逐步解說：SharePoint Designer 可重複使用工作流程匯入 Visual Studio
  本逐步解說示範如何匯入 SharePoint Designer 2010 中建立可重複使用工作流程[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 工作流程專案。  
  
 在 SharePoint Designer 中建立的工作流程或*宣告式工作流程*，組成[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]陳述式，而非程式碼。 SharePoint Designer 2010 引進*可重複使用的工作流程*，這是可由不同的清單，在 SharePoint 網站中的可移植的宣告式工作流程。  
  
 在中建立的工作流程[!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]，例如循序和狀態機器工作流程，會呼叫*程式碼工作流程*。 程式碼工作流程是由 XML 檔案和使用者可以自訂工作流程的行為的程式碼模組所組成。  
  
 Visual Studio 可讓您匯入 SharePoint Designer 2010 中建立之可重複使用的工作流程，並將它們轉換成程式碼工作流程，以便在 SharePoint 網站中使用。  
  
 本逐步解說將示範下列工作：  
  
- 在 SharePoint Designer 中建立簡單、 可重複使用工作流程。  
  
- 匯出至 SharePoint Designer 可重複使用工作流程 *.wsp*檔案到 SharePoint。  
  
- 匯入 *.wsp*檔案載入[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]使用匯入可重複使用工作流程專案。  
  
- 加入程式碼變更工作流程。  
  
- 在 SharePoint 網站中使用匯入的工作流程。  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的版本[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]和 SharePoint。  
  
-   Visual Studio。  
  
-   Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010。  
  
## <a name="create-target-sharepoint-subsites"></a>建立目標 SharePoint 子網站
 首先您必須建立兩個新的 SharePoint 子網站： 一個用來裝載可重複使用的工作流程，從 SharePoint Designer，另一個是用來裝載已轉換的工作流程。  
  
#### <a name="to-create-sharepoint-subsites"></a>若要建立 SharePoint 子網站  
  
1. 在 SharePoint Designer 2010 中，在功能表列上選擇**檔案** > **新增空白網站**。  
  
2. 在 **新增空白網站** 對話方塊中，瀏覽至 SharePoint 網站，您想要用來建立工作流程，或使用 http:// 的值<em>SystemName</em>/，然後選擇 **確定**按鈕。  
  
    首頁隨即出現。  
  
3. 在 [**子**區段中，選擇**新增**] 按鈕。  
  
4. 在**新增**對話方塊方塊中，選擇**SharePoint 範本**從左窗格中的清單，然後選擇 **小組網站**從右窗格中的清單。  
  
5. 在**指定網站的位置**方塊中，將 word**子網站**URL 中**SPD1**，然後選擇**確定**  按鈕。  
  
    這會開啟新的子網站，到 SharePoint Designer。 關閉 SharePoint Designer 的這個執行個體，並返回第一個執行個體 （最上層站台）。  
  
6. 重複步驟 3-5 來建立第二個的子網站，這次是取代單字**subsite**中[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]具有**SPD2**。  
  
## <a name="create-a-sharepoint-designer-reusable-workflow"></a>建立 SharePoint Designer 可重複使用工作流程
 因為 SharePoint 不包含任何可重複使用的工作流程，您可以使用此範例中，您會建立一個。 在此簡單的工作流程，當使用者有特定的標題，工作清單 中輸入新的工作的工作會指派給該使用者。  
  
#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>若要建立 SharePoint Designer 可重複使用工作流程
  
1.  在 **子**區段中，選擇**SPD1**網站進行修改。  
  
2.  在功能區中，選擇**可重複使用工作流程** 按鈕。  
  
     建立可重複使用工作流程精靈隨即出現。  
  
3.  在 **名稱**方塊中，輸入**SPD Task Workflow**。  
  
4.  在 **內容類型**清單中，選擇**工作**，然後選擇  **確定**按鈕。  
  
     在 SharePoint Designer 工作流程設計工具中，開啟工作流程。  
  
5.  在工作流程設計工具中，選擇 [步驟 1，然後，在功能區中，選擇**條件**] 按鈕。  
  
6.  在條件清單中，選擇**如果目前的項目欄位等於值**。  
  
     這個步驟會加入名為條件**如果欄位等於值**。  
  
7.  在 **如果欄位等於值**條件中，選擇**欄位**連結。  
  
8.  在值清單中，選擇**Title**。  
  
9. 在 **如果欄位等於值**條件中，選擇**值**連結。  
  
10. 在方塊中，輸入**新的工作**。  
  
     條件陳述式現在會讀取**如果目前項目： 標題等於新工作**。  
  
11. 選擇條件陳述式下的那一行，然後在功能區中，選擇**動作** 按鈕。  
  
12. 在動作清單中，選擇**目前的項目中的集合欄位**。  
  
13. 在 **值的集合欄位**動作，選擇**欄位**連結，然後在清單中，選擇**指派給**。  
  
14. 在**值的集合欄位**動作，選擇**值**連結，然後在現有的使用者和群組的清單中，選擇**建立之項目的使用者**。  
  
15. 選擇**新增**按鈕，然後再選擇**確定** 按鈕。  
  
     Action 陳述式現在會讀取**將設定指派給以目前項目： CreatedBy**。  
  
## <a name="save-and-deploy-the-reusable-workflow"></a>儲存並部署可重複使用的工作流程
 因為[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]可以只匯入 *.wsp*檔案，您必須將儲存為可重複使用的工作流程 *.wsp*檔案，並將它部署到 SharePoint 中，然後再匯入到[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
> [!IMPORTANT]  
>  如果您收到執行階段錯誤，執行下列程序，您必須對 SharePoint 網站存取的系統上執行程序。  
  
#### <a name="to-save-and-deploy-the-reusable-workflow"></a>若要儲存並部署可重複使用的工作流程  
  
1.  在 SharePoint Designer 頂端，選擇**儲存**按鈕以儲存您的進度，然後選擇**發佈**按鈕，將部署工作流程**SPD1** SharePoint 網站.  
  
2.  在 [導覽] 窗格中，選擇**工作流程**物件。  
  
3.  底下**可重複使用工作流程**，選擇**SPD Task Workflow**。  
  
4.  在功能區中，選擇**另存為範本**按鈕以儲存工作流程作為 *.wsp*檔案。  
  
5.  開啟**SPD1**瀏覽器檢視中的 SharePoint 網站 *.wsp*在 SharePoint 中的檔案。  
  
6.  在 [快速啟動] 列中，選擇**程式庫**連結。  
  
7.  在 **文件庫**區段中，選擇**網站資產**連結。  
  
     **SPD Task Workflow**檔案會列在與其他站台的資產。  
  
8.  在檔案清單中，選擇該檔案的名稱  
  
9. 在 [**檔案下載**對話方塊方塊中，選擇**儲存**] 按鈕以儲存 *.wsp*在您的本機系統上的檔案。  
  
## <a name="import-the-wsp-file-into-visual-studio"></a>.Wsp 檔案匯入 Visual Studio
 匯入 *.wsp*檔案載入[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]使用匯入可重複使用工作流程專案。 此專案會將工作流程從可重複使用、 宣告式工作流程轉換成程式碼工作流程。 工作流程轉換之後，您將使用的程式碼來修改其行為。  
  
#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>若要從.wsp 檔案匯入工作流程，並加以修改  
  
1. 在  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，在功能表列上選擇**檔案** > **新增** > **專案**。  
  
2. 在**新的專案**對話方塊方塊中，展開**SharePoint**之下的節點**Visual C#** 或**Visual Basic**，然後選擇  **2010年**節點。  
  
3. 中**範本**窗格中，選擇**匯入可重複使用 SharePoint 2010 工作流程**範本中，保留做為專案名稱**WorkflowImportProject1**，然後選擇**確定** 按鈕。  
  
    SharePoint 自訂精靈 隨即出現。  
  
4. 在 **指定偵錯的網站和安全性層級**頁面上，輸入[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]與您先前建立的第二個 SharePoint 子網站： http://<em>系統名稱</em>/SPD2。  
  
5. 在 **此 SharePoint 方案的信任層級為何？** 區段中，選擇**部署為伺服陣列方案**選項按鈕，然後選擇**下一步**  按鈕。  
  
    如需有關沙箱和伺服器陣列方案，請參閱[沙箱化方案考量](../sharepoint/sandboxed-solution-considerations.md)。  
  
6. 在 [**指定新專案來源**頁面上，瀏覽至您先前儲存在系統上位置 *.wsp*檔案，開啟檔案，然後選擇**下一步]** 按鈕。  
  
   > [!NOTE]  
   >  選擇**完成**按鈕以匯入中的所有可用項目 *.wsp*檔案。  
  
    這會顯示一份可供匯入可重複使用工作流程。  
  
7. 在**選取要匯入項目**方塊中，選擇**SPD Task Workflow**工作流程，然後選擇**完成** 按鈕。  
  
    匯入作業完成之後，專案名為**WorkflowImportProject1**會建立包含名為工作流程**SPD_Workflow_TestFT**。 在此資料夾是工作流程的定義檔*Elements.xml*和 工作流程設計工具檔案 (*.xoml*)。 設計工具包含兩個檔案： 規則檔案 (.rules) 和程式碼後置檔案 (任一 *.cs*或是 *.vb*，取決於您的專案的程式設計語言)。  
  
8. 在 **方案總管**，刪除**其他匯入檔案**資料夾。  
  
9. 在  *Elements.xml*檔案，請刪除`InstantiationURL="_layouts/IniErkflIP.sspx"`。  
  
10. 在 **方案總管**，選擇**WorkflowImportProject1**，然後在功能表列上選擇 **專案** > **設定為啟始專案**來設定**WorkflowImportProject1**為啟動項目。  
  
     只有在您偵錯專案時，立即，這會顯示清單。  
  
11. 因為**匯入的可重複使用 SharePoint 2010 工作流程**範本不會匯入匯入的工作流程的關聯屬性值，您必須輸入它們。 做法：  
  
    1.  在 **方案總管**，選擇**SPD_Workflow_TestFT**節點。  
  
    2.  選擇省略符號 (![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")) 按鈕旁的清單屬性，其中一個這類**目標清單**屬性。  
  
    3.  填滿遺漏值，在 SharePoint 自訂精靈，然後選擇 **完成** 按鈕。  
  
12. 選擇.xoml 檔案]，然後在功能表列上選擇 [**檢視** > **設計師**若要在工作流程設計工具中檢視匯入的工作流程。  
  
13. 在  **Windows Workflow v3.0**節點**工具箱**，執行下列步驟：  
  
    - 開啟捷徑功能表**程式碼**活動，然後選擇**複製**。 在工作流程設計工具中，開啟 在下一行的捷徑功能表**SequenceActivity1**活動，然後選擇**貼上**。  
  
    - 拖曳**程式碼**活動，從**工具箱**工作流程設計工具中，並將它連接到下一行**SequenceActivity1**活動。  
  
      這將活動加入至名為工作流程設計工具**CodeActivity1**。 在這個活動中，您將建立公告的公告清單中，當使用者開始工作流程的程式碼動作。  
  
14. 請執行下列其中一組步驟：  
  
    -   按兩下**CodeActivity1**產生事件處理常式，並檢視程式碼。  
  
    -   在 **屬性**視窗**CodeActivity1**，設定的值**ExecuteCode**屬性設**codeActivity_ExecuteCode**。  
  
15. 現有下新增下列**使用**或是**匯入**陳述式：  
  
     [!code-csharp[SP_SPDWFImport#1](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]  
  
16. 取代`codeActivity1_ExecuteCode`取代下列項目：  
  
     [!code-csharp[SP_SPDWFImport#2](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]  
  
## <a name="deploy-the-project-and-associate-the-workflow"></a>部署專案和工作流程產生關聯
 接下來，執行 WorkflowImportProject1 將它部署到 SharePoint 網站，並將關聯即可檢視和測試修改過的 [工作] 清單中的工作流程轉換成工作流程。  
  
#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>若要部署專案和工作流程產生關聯  
  
1.  在  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，選擇**F5**鍵執行並部署轉換後的工作流程專案。  
  
2.  在 [快速啟動] 列中，選擇**任務**連結可以顯示 [工作] 清單。  
  
3.  在上**清單工具**索引標籤上，選擇**項目**按鈕，然後再選擇**新項目** 按鈕。  
  
     **工作-新的項目**對話方塊隨即開啟。  
  
4.  在 **標題**方塊中，輸入**新工作**，然後選擇 **儲存**按鈕。  
  
5.  在 [**清單工具**索引標籤上，選擇**清單**按鈕，然後再選擇**清單設定**] 按鈕。  
  
     **清單設定**頁面隨即出現。  
  
6.  在 **權限與管理**區段中，選擇**工作流程設定**連結。  
  
     **工作流程設定**頁面隨即出現。  
  
7.  選擇**新增的工作流程**連結。  
  
8.  在 **工作流程**清單中，選擇**WorkflowImportProject1-SPD Workflow Test**。  
  
9. 在 [**名稱**方塊中，輸入**SPD Workflow Test**，然後選擇 **[確定]** ] 按鈕。  
  
10. 在 [快速啟動] 列中，選擇**任務**清單。  
  
11. 選擇箭號旁**新的工作**，然後在清單中，選擇 **工作流程**。  
  
12. 中**啟動新的工作流程**區段中，選擇連結**SPD Workflow Test**，然後選擇**啟動**按鈕來起始工作流程。  
  
    > [!NOTE]  
    >  或者，您可以自動為相關聯的工作流程清單藉由執行工作流程設定精靈，並設定自動產生關聯的工作流程。  
  
     請注意兩個動作由工作流程： 您的名稱會出現在工作的**指派給**資料行，且宣告會出現在**公告**清單。  
  
## <a name="see-also"></a>另請參閱
 [從現有的 SharePoint 網站匯入項目](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)   
 [建立可重複使用的控制項，為 web 組件或應用程式頁面](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
