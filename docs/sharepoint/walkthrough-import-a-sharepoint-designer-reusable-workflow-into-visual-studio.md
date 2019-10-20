---
title: 逐步解說：將 SharePoint Designer 可重複使用的工作流程匯入 Visual Studio |Microsoft Docs
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9924b3d709f882fdd552708a795a4b23bd22b070
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665406"
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio"></a>逐步解說：將 SharePoint Designer 可重複使用的工作流程匯入 Visual Studio
  本逐步解說示範如何將 SharePoint Designer 2010 中建立的可重複使用工作流程匯入 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 工作流程專案中。

 在 SharePoint Designer 或*宣告式工作流程*中建立的工作流程包含 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 語句，而不是程式碼。 SharePoint Designer 2010 引進可*重複使用的工作流程*，也就是可供 SharePoint 網站中不同清單使用的可移植、宣告式工作流程。

 在 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] 中建立的工作流程（例如，順序和狀態機器工作流程）稱為「程式*代碼工作流程*」。 程式碼工作流程是由 XML 檔案和程式碼模組所組成，使用者可以在其中自訂工作流程的行為。

 Visual Studio 可讓您匯入 SharePoint Designer 2010 中建立之可重複使用的工作流程，並將它們轉換成程式碼工作流程，以便在 SharePoint 網站中使用。

 本逐步解說將示範下列工作：

- 在 SharePoint Designer 中建立簡單、可重複使用的工作流程。

- 將 SharePoint Designer 可重複使用的工作流程匯出至 *.wsp*檔案和 sharepoint。

- 使用 [匯入可重複使用的工作流程] 專案，將 *.wsp*檔案匯入 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

- 藉由加入程式碼來修改工作流程。

- 在 SharePoint 網站中使用匯入的工作流程。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisites
 您需要下列元件才能完成此逐步解說：

- 支援的 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] 和 SharePoint 版本。

- Visual Studio。

- Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010。

## <a name="create-target-sharepoint-subsites"></a>建立目標 SharePoint 子網站
 首先，您會建立兩個新的 SharePoint 子網站：一個用來裝載 SharePoint Designer 中可重複使用的工作流程，另一個裝載轉換的工作流程。

#### <a name="to-create-sharepoint-subsites"></a>若要建立 SharePoint 子網站

1. 在 SharePoint Designer 2010 的功能表列上 **，選擇 [** 檔案]  >  [**新的空白網站**]。

2. 在 [**新的空白網站**] 對話方塊中，流覽至您要建立工作流程的 SharePoint 網站，或使用 HTTP://<em>SystemName</em>/的值，然後選擇 [**確定]** 按鈕。

    首頁隨即出現。

3. 在 [**子網站**] 區段中，選擇 [**新增**] 按鈕。

4. 在 [**新增**] 對話方塊中，從左窗格的清單中選擇 [ **SharePoint 範本**]，然後從右窗格的清單中選擇 [**小組網站**]。

5. 在 [**指定網站的位置**] 方塊中，以**SPD1**取代 URL 中的 [**子網站**]，然後選擇 [**確定]** 按鈕。

    這會在 SharePoint Designer 中開啟新的子網站。 關閉這個 SharePoint Designer 實例，然後返回第一個實例（頂層網站）。

6. 重複步驟 3-5 來建立第二個子網站，這次以**SPD2**取代 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] 中的文字**子網站**。

## <a name="create-a-sharepoint-designer-reusable-workflow"></a>建立 SharePoint Designer 可重複使用的工作流程
 因為 SharePoint 不包含可供您用於此範例的任何可重複使用工作流程，所以您會建立一個。 在這個簡單的工作流程中，當使用者在具有特定標題的工作清單中輸入新工作時，會將工作指派給該使用者。

#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>建立 SharePoint Designer 可重複使用的工作流程

1. 在 [**子網站**] 區段中，選擇要修改的**SPD1**網站。

2. 在功能區上，選擇 [**可重複使用的工作流程**] 按鈕。

     [建立可重複使用的工作流程] wizard 隨即出現。

3. 在 [**名稱**] 方塊中，輸入**SPD Task Workflow**。

4. 在 [**內容類型**] 清單中 **，選擇 [** 工作]，然後選擇 [**確定]** 按鈕。

     工作流程會在 SharePoint Designer 工作流程設計工具中開啟。

5. 在工作流程設計工具中，選擇 [步驟 1]，然後在功能區上選擇 [**條件**] 按鈕。

6. 在條件清單中，選擇 [**目前專案] 欄位是否等於 [值**]。

     此步驟會新增名為 [**如果欄位等於值**] 的條件。

7. 在 [**如果欄位等於值**] 條件中，選擇 [**欄位**] 連結。

8. 在值清單中，選擇 [**標題**]。

9. 在 [**如果欄位等於值**] 條件中，選擇 [**值**] 連結。

10. 在方塊中，輸入**New task**。

     條件陳述式現在會讀取**目前的專案：標題等於新**工作。

11. 選擇 [條件] 語句底下的那一行，然後在功能區上選擇 [**動作**] 按鈕。

12. 在動作清單中，選擇 [**在目前專案中設定欄位**]。

13. 在 [**將欄位設定為值**] 動作中，選擇 [**欄位**] 連結，然後在清單中選擇 [**指派**給]。

14. 在 [**將欄位設定為值**] 動作中，選擇 [**值**] 連結，然後在 [現有使用者和群組] 清單中，選擇 [**建立專案的使用者**]。

15. 選擇 [**新增**] 按鈕，然後選擇 [**確定]** 按鈕。

     Action 語句現在會**將 Set 指派至讀入目前的專案： CreatedBy**。

## <a name="save-and-deploy-the-reusable-workflow"></a>儲存並部署可重複使用的工作流程
 因為 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 只能匯入 *.wsp*檔案，所以您必須將可重複使用的工作流程儲存為 *.wsp*檔案，然後將它部署到 SharePoint，然後再匯入至 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

> [!IMPORTANT]
> 如果您在執行下列程式時收到執行階段錯誤，您必須在可存取 SharePoint 網站的系統上執行此程式。

#### <a name="to-save-and-deploy-the-reusable-workflow"></a>儲存和部署可重複使用的工作流程

1. 在 SharePoint Designer 的頂端，選擇 [**儲存**] 按鈕以儲存您的進度，然後選擇 [**發佈**] 按鈕，將工作流程部署至**SPD1** SharePoint 網站。

2. 在流覽窗格中，選擇 [**工作流程**] 物件。

3. 在 [**可重複使用的工作**流程] 下選擇 [ **SPD 工作流程**]。

4. 在功能區上，選擇 [**另存為範本**] 按鈕，將工作流程儲存為 *.wsp*檔案。

5. 在瀏覽器中開啟**SPD1** SharePoint 網站，以在 SharePoint 中查看 *.wsp*檔案。

6. 在 [快速啟動] 列上，選擇 [文檔**庫**] 連結。

7. 在 [**文件庫**] 區段中，選擇 [**網站資產**] 連結。

     **SPD 工作流程**檔案會與其他網站資產一併列出。

8. 在檔案清單中，選擇該檔案的名稱

9. 在 [檔案**下載**] 對話方塊中，選擇 [**儲存**] 按鈕，將 *.wsp*檔案儲存在本機系統上。

## <a name="import-the-wsp-file-into-visual-studio"></a>將 .wsp 檔案匯入 Visual Studio
 藉由使用 [匯入可重複使用的工作流程] 專案，將 *.wsp*檔案匯入 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 此專案會將工作流程從可重複使用的宣告式工作流程轉換成程式碼工作流程。 轉換工作流程之後，您將會使用程式碼來修改其行為。

#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>從 .wsp 檔案匯入工作流程並加以修改

1. 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 的功能表列上 **，選擇 [** 檔案] [檔案] [ > **新增** > **專案**]。

2. 在 [**新增專案**] 對話方塊中，展開 [**視覺效果C#**  ] 或 [ **Visual Basic**] 底下的 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

3. 在 [**範本**] 窗格中，選擇 [匯**入可重複使用的 SharePoint 2010 工作流程**] 範本，將專案的名稱保留為**WorkflowImportProject1**，然後選擇 [**確定]** 按鈕。

    [SharePoint 自訂嚮導] 隨即出現。

4. 在 [**指定網站和安全性層級進行調試**程式] 頁面上，輸入您先前建立之第二個 SharePoint 子網站的 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]： HTTP://<em>系統名稱</em>/SPD2。

5. 在 [**此 SharePoint 方案的信任層級為何？** ] 區段中，選擇 [**部署為數組方案**] 選項按鈕，然後選擇 [**下一步]** 按鈕。

    如需沙箱與伺服器陣列方案的詳細資訊，請參閱[沙箱化方案考慮](../sharepoint/sandboxed-solution-considerations.md)。

6. 在 [**指定新專案來源**] 頁面中，流覽至您先前儲存 *.wsp*檔案之系統上的位置，開啟檔案，然後選擇 [**下一步]** 按鈕。

   > [!NOTE]
   > 選擇 [**完成]** 按鈕，以匯入 *.wsp*檔案中的所有可用專案。

    這會顯示可重複使用的工作流程清單，以供匯入。

7. 在 [**選取要匯入的專案**] 方塊中，選擇 [ **SPD Task workflow** ] 工作流程，然後選擇 [**完成]** 按鈕。

    匯入作業完成後，會建立名為**WorkflowImportProject1**的專案，其中包含名為**SPD_Workflow_TestFT**的工作流程。 在此資料夾中，是工作流程的定義檔*元素 .xml*和工作流程設計工具檔案（ *. xoml*）。 設計工具組含兩個檔案：規則檔（. 規則）和程式碼後置檔案（ *.cs*或 *.vb*，視您專案的程式設計語言而定）。

8. 在**方案總管**中，刪除 [**其他匯入**檔案] 資料夾。

9. 在*元素 .xml*檔案中，刪除 `InstantiationURL="_layouts/IniErkflIP.sspx"`。

10. 在**方案總管**中，選擇 [ **WorkflowImportProject1**]，然後在功能表列上選擇 [**專案** > **設定為啟始專案**]，將**WorkflowImportProject1**設定為啟始專案。

     這會在您進行專案的調試時立即顯示清單。

11. 因為「匯**入可重複使用的 SharePoint 2010 工作流程**」範本不會匯入所匯入工作流程的關聯屬性值，所以您必須輸入它們。 若要這樣做：

    1. 在**方案總管**中，選擇 [ **SPD_Workflow_TestFT** ] 節點。

    2. 選擇其中一個清單屬性旁的省略號（![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")）按鈕，例如 [**目標清單**] 屬性。

    3. 在 [SharePoint 自訂嚮導] 中填入遺漏值，然後選擇 [**完成]** 按鈕。

12. 選擇 xoml 檔案，然後在功能表列上選擇 [ **view**  > **Designer** ]，在工作流程設計工具中查看匯入的工作流程。

13. 在 [**工具箱**] 的 [ **Windows Workflow v3.0** ] 節點中，執行下列其中一個步驟：

    - 開啟 [程式**代碼**] 活動的快捷方式功能表，然後選擇 [**複製**]。 在工作流程設計工具中，開啟 [ **sequenceactivity1 那一行**] 活動底下行的快捷方式功能表，然後選擇 [**貼**上]。

    - 將 [程式**代碼**] 活動從 [工具箱] 拖曳至工作流程設計**工具**，並將它連接到 [ **sequenceactivity1 那一行**] 活動底下的那一行。

      這會將活動新增至名為**CodeActivity1**的工作流程設計工具。 在此活動中，您將新增程式碼動作，在使用者啟動工作流程時，于 [公告] 清單中建立通知。

14. 請執行下列其中一組步驟：

    - 按兩下 [ **CodeActivity1** ] 以產生事件處理常式，並查看程式碼。

    - 在**CodeActivity1**的 [**屬性**] 視窗中，將**ExecuteCode**屬性的值設定為**codeActivity_ExecuteCode**。

15. 在現有的**using**或**Imports**指示詞底下新增下列內容：

     [!code-csharp[SP_SPDWFImport#1](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]

16. 將 `codeActivity1_ExecuteCode` 取代為下列內容：

     [!code-csharp[SP_SPDWFImport#2](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]

## <a name="deploy-the-project-and-associate-the-workflow"></a>部署專案並建立工作流程的關聯
 接下來，執行 WorkflowImportProject1 以將其部署至 SharePoint 網站，然後將工作流程與 Tasks 清單建立關聯，以查看並測試已修改、已轉換的工作流程。

#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>若要部署專案並建立工作流程的關聯

1. 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中，選擇**F5**鍵以執行並部署轉換後的工作流程專案。

2. 在 [快速啟動] 列上，選擇 [工作] 連結以顯示 **[工作]** 清單。

3. 在 [**清單工具**] 索引標籤上，選擇 [**專案**] 按鈕，然後選擇 [**新增專案**] 按鈕。

     [工作 **-新專案**] 對話方塊隨即開啟。

4. 在 [**標題**] 方塊中，輸入**New task**，然後選擇 [**儲存**] 按鈕。

5. 在 [**清單工具**] 索引標籤上，選擇 [**清單**] 按鈕，然後選擇 [**清單設定**] 按鈕。

     [**清單設定**] 頁面隨即出現。

6. 在 [**許可權與管理**] 區段中，選擇 [**工作流程設定**] 連結。

     [**工作流程設定**] 頁面隨即出現。

7. 選擇 [**新增工作流程**] 連結。

8. 在 [**工作流程**] 清單中，選擇 [ **WorkflowImportProject1-SPD Workflow Test**]。

9. 在 [**名稱**] 方塊中，輸入「 **SPD 工作流程測試**」，然後選擇 [**確定]** 按鈕。

10. 在 **[快速啟動] 列中**，選擇 [工作] 清單。

11. 選擇 [**新** **工作**] 旁邊的箭號，然後在清單中選擇 [workflow]。

12. 在 [**開始新的工作流程**] 區段中，選擇 [ **SPD 工作流程測試**] 的連結，然後選擇 [**啟動**] 按鈕以起始工作流程。

    > [!NOTE]
    > 或者，您可以執行 [工作流程設定] 嚮導並將工作流程設定為 [自動關聯]，以自動將工作流程與清單建立關聯。

     請注意，工作流程會執行兩個動作：您的名稱會出現在工作的 [**指派至**] 欄位中，而**公告清單中會出現宣告。**

## <a name="see-also"></a>請參閱
- [從現有的 SharePoint 網站匯入專案](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
- [為 web 元件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
