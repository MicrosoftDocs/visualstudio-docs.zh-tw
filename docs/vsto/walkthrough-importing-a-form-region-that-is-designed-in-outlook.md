---
title: 逐步解說：匯入在 Outlook 中設計的表單區域
description: 瞭解如何在 Microsoft Outlook 中設計表單區域，然後使用 [新增表單區域] 嚮導，將表單區域匯入至 Outlook VSTO 增益集專案。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- importing form regions
- form regions [Office development in Visual Studio], importing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9b65502bbf29f6e0df7435f6a27d3c51e8082e41
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97522675"
---
# <a name="walkthrough-import-a-form-region-that-is-designed-in-outlook"></a>逐步解說：匯入在 Outlook 中設計的表單區域
  本逐步解說示範如何在 Microsoft Office Outlook 中設計表單區域，然後使用 [新增表單區域精靈]  將表單區域匯入至 Outlook VSTO 增益集專案。 在 Outlook 中設計表單區域可讓您將原生 Outlook 控制項加入繫結至 Outlook 資料的表單區域。 匯入表單區域之後，即可處理每個控制項的事件。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 本逐步解說將說明下列工作：

- 使用 Outlook 中的表單區域設計工具設計表單區域。

- 將表單區域匯入至 Outlook VSTO 增益集專案。

- 處理表單區域上的控制項事件。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] 或 [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="design-a-form-region-by-using-the-form-region-designer-in-outlook"></a>使用 Outlook 中的表單區域設計工具設計表單區域
 在這個步驟中，您將在 Outlook 中設計表單區域。 然後您會將表單區域儲存到容易找到的位置，以便匯入至 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

 這個範例表單區域會完全取代慣用的工作表單。 它提供一種方法，來追蹤必須先完成才能執行主要工作之所有工作 (必要工作) 的進度。 這個表單區域會顯示必要工作清單，並顯示清單中每項工作的完成狀態。 使用者可以將工作加入清單並加以移除， 也可以重新整理每項工作的完成狀態。

### <a name="to-design-a-form-region-by-using-the-form-region-designer-in-outlook"></a>使用 Outlook 中的表單區域設計工具設計表單區域

1. 啟動 Microsoft Office Outlook。

2. 在 Outlook 的 [開發人員]  索引標籤上，按一下 [設計表單] 。 如需詳細資訊，請參閱 [如何：在功能區顯示開發人員](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)索引標籤。

3. 在 [設計表單]  方塊中，按一下 [工作] ，然後按一下 [開啟] 。

4. 在 Outlook 的 [開發人員]  索引標籤上，按一下 [設計]  群組中的 [新增表單區域] 。

     新的表單區域隨即開啟。 如果 [欄位選擇]  未出現，請按一下 [工具]  群組中的 [欄位選擇]  。

5. 將 [主旨]  欄位和 [完成率]  欄位從 [欄位選擇]  拖曳至表單區域。

6. 在 [工具]  群組中，按一下 [控制工具箱]  開啟 [工具箱] 。

7. 將標籤從 [工具箱]  拖曳至表單區域。 將標籤置於 [主旨]  和 [完成率]  欄位下方。

8. 以滑鼠右鍵按一下標籤，然後按一下 [進階屬性] 。

9. 在 [屬性]  視窗中，將 [標題]  屬性設定為「這項工作相依於下列工作」 ，將 [寬度]  屬性設定為 **200**，然後按一下 [套用] 。

10. 將 ListBox 控制項從 [工具箱]  拖曳至表單區域。 將清單方塊置於 [這項工作相依於下列工作]  標籤下方。

11. 選取您剛才加入的清單方塊。

12. 在 [屬性]  視窗中，將 [寬度]  設定為 **300**，然後按一下 [套用] 。

13. 將標籤從 [工具箱]  拖曳至表單區域。 將標籤置於清單方塊下方。

14. 選取您剛才加入的標籤。

15. 在 [屬性]  視窗中，將 [標題]  屬性設定為「選取要加入相依工作清單的工作」 ，將 [寬度]  屬性設定為 **200**，然後按一下 [套用] 。

16. 將 ComboBox 控制項從 [工具箱]  拖曳至表單區域。 將下拉式方塊置於 [選取要加入相依工作清單的工作]  標籤下方。

17. 選取您剛才加入的下拉式方塊。

18. 在 [屬性]  視窗中，將 [寬度]  屬性設定為 **300**，然後按一下 [套用] 。

19. 將 CommandButton 控制項從 [工具箱]  拖曳至表單區域。 將命令按鈕置於下拉式方塊一旁。

20. 選取您剛才加入的命令按鈕。

21. 在 [屬性]  視窗中，將 [名稱]  設定為 **AddDependentTask**，將 [標題]  設定為「加入相依工作」 ，將 [寬度]  設定為 **100**，然後按一下 [套用] 。

22. 在 [欄位選擇] 中，按一下 [新增] 。

23. 在 [新增欄位]  對話方塊的 [名稱]  欄位中，輸入 **hiddenField** ，然後按一下 [確定] 。

24. 將 [hiddenField]  欄位從 [欄位選擇]  拖曳至表單區域。

25. 在 [屬性]  視窗中，將 [可見]  設定為 [0 - False] ，然後按一下 [套用] 。

26. 在 Outlook 的 [開發人員]  索引標籤上，按一下 [設計]  群組中的 [儲存]  按鈕，然後按一下 [另存表單區域為] 。

     將表單區域命名為 **TaskFormRegion** ，並將其儲存到您電腦上的本機目錄中。

     Outlook 會將表單區域儲存為 Outlook 表單儲存體 (*.ofs*) 檔。 表單區域會以名稱 *TaskFormRegion* 儲存。

27. 結束 Outlook。

## <a name="create-a-new-outlook-add-in-project"></a>建立新的 Outlook 增益集專案
 在這個步驟中，您將建立 Outlook VSTO 增益集專案。 在本逐步解說稍後，您會將表單區域匯入至專案。

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>建立新的 Outlook VSTO 增益集專案

1. 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中，建立名為 **TaskAddIn** 的 Outlook VSTO 增益集專案。

2. 在 [新增專案]  對話方塊中，選取 [為方案建立目錄] 。

3. 將專案儲存至預設的專案目錄。

     如需詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

## <a name="import-the-form-region"></a>匯入表單區域
 您可以使用 [新的 Outlook 表單區域精靈]  ，將您在 Outlook 中設計的表單區域匯入至 Outlook VSTO 增益集專案。

### <a name="to-import-the-form-region-into-the-outlook-vsto-add-in-project"></a>將表單區域匯入至 Outlook VSTO 增益集專案

1. 在 [方案總管] 中，以滑鼠右鍵按一下 **TaskAddIn** 專案，指向 [加入] ，然後按一下 [新增項目] 。

2. 在 [範本]  窗格中，選取 [Outlook 表單區域] ，將檔案命名為 **TaskFormRegion**，然後按一下 [加入] 。

     [ **NewOutlook] 表單區域** wizard 隨即啟動。

3. 在 [選取您希望如何建立此表單區域]  頁面上，按一下 [匯入 Outlook 表單儲存區 (.ofs) 檔案] ，然後按一下 [瀏覽] 。

4. 在 [現有 Outlook 表單區域檔案位置]  對話方塊中，瀏覽至 *TaskFormRegion.ofs* 的位置並選取 **TaskFormRegion.ofs**，然後依序按一下 [開啟] 和 [下一步] 。

5. 在 [選取要建立的表單區域類型]  頁面上，按一下 [全部取代] ，然後按 [下一步] 。

     「全部取代」  (Replace-All) 表單區域會取代整個 Outlook 表單。 如需表單區欄位型別的詳細資訊，請參閱 [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)。

6. 在 [提供描述文字和選取顯示設定]  頁面上，按 [下一步] 。

7. 在 [識別將顯示此表單區域的訊息類別]  頁面的 [將顯示此表單區域的自訂訊息類別為何]  欄位中，輸入 **IPM.Task.TaskFormRegion**，然後按一下 [完成] 。

     系統會將 *TaskFormRegion.cs* 或 *TaskFormRegion .vb* 檔案新增至您的專案。

## <a name="handle-the-events-of-controls-on-the-form-region"></a>處理表單區域上的控制項事件
 現在專案中已有表單區域，您可以加入程式碼來處理 Outlook 表單區域中所加入按鈕的 `Microsoft.Office.Interop.Outlook.OlkCommandButton.Click` 事件。

 此外，您也可以將程式碼加入 <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> 事件，以便在表單區域出現時更新表單區域上的控制項。

### <a name="to-handle-the-events-of-controls-on-the-form-region"></a>處理表單區域上的控制項事件

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [ *TaskFormRegion.cs* ] 或 [ *TaskFormRegion*]，然後按一下 [ **視圖程式碼**]。

    *TaskFormRegion.cs* 或 *TaskFormRegion* 會在程式碼編輯器中開啟。

2. 將下列程式碼新增至 `TaskFormRegion` 類別。 這個程式碼會以 Outlook [工作] 資料夾中每項工作的主旨列，填入表單區域上的下拉式方塊。

    [!code-csharp[Trin_Outlook_FR_Import#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#1)]
    [!code-vb[Trin_Outlook_FR_Import#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#1)]

3. 將下列程式碼新增至 `TaskFormRegion` 類別。 此程式碼會執行下列工作：

   - 在 [工作] 資料夾中呼叫 `FindTaskBySubjectName` Helper 方法並傳遞所需工作的主旨，藉此尋找 `Microsoft.Office.Interop.Outlook.TaskItem`。 您將在下一個步驟中加入 `FindTaskBySubjectName` Helper 方法。

   - 將 `Microsoft.Office.Interop.Outlook.TaskItem.Subject` 和 `Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete` 值加入相依工作清單方塊。

   - 將工作的主旨加入表單區域上的隱藏欄位。 隱藏欄位會將這些值儲存為 Outlook 項目的一部分。

     [!code-csharp[Trin_Outlook_FR_Import#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#2)]
     [!code-vb[Trin_Outlook_FR_Import#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#2)]

4. 將下列程式碼新增至 `TaskFormRegion` 類別。 這個程式碼提供上一個步驟所述的 Helper 方法 `FindTaskBySubjectName` 。

    [!code-csharp[Trin_Outlook_FR_Import#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#3)]
    [!code-vb[Trin_Outlook_FR_Import#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#3)]

5. 將下列程式碼新增至 `TaskFormRegion` 類別。 此程式碼會執行下列工作：

   - 以每項相依工作的目前完成狀態，重新整理表單區域上的清單方塊。

   - 剖析隱藏的文字欄位，以取得每項相依工作的主旨。 然後藉 `Microsoft.Office.Interop.Outlook.TaskItem` 由呼叫 `FindTaskBySubjectName` helper 方法並傳遞每項工作的主旨，在 [工作] 資料夾中尋找每個。

   - 將 `Microsoft.Office.Interop.Outlook.TaskItem.Subject` 和 `Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete` 值加入相依工作清單方塊。

     [!code-csharp[Trin_Outlook_FR_Import#4](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#4)]
     [!code-vb[Trin_Outlook_FR_Import#4](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#4)]

6. 以下列程式碼取代 `TaskFormRegion_FormRegionShowing` 事件處理常式。 此程式碼會執行下列工作：

   - 在表單區域出現時，以工作主旨填入表單區域上的下拉式方塊。

   - 在表單區域出現時，呼叫 `RefreshTaskListBox` Helper 方法。 這會顯示之前開啟項目時，加入清單方塊的任何相依工作。

     [!code-csharp[Trin_Outlook_FR_Import#5](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#5)]
     [!code-vb[Trin_Outlook_FR_Import#5](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#5)]

## <a name="test-the-outlook-form-region"></a>測試 Outlook 表單區域
 若要測試表單區域，請將工作加入表單區域上的必要工作清單。 更新必要工作的完成狀態，然後檢視必要工作清單中更新的工作完成狀態。

### <a name="to-test-the-form-region"></a>測試表單區域

1. 按 **F5** 執行專案。

     Outlook 啟動。

2. 在 Outlook 的 [常用]  索引標籤上，按一下 [新項目] ，然後按一下 [工作] 。

3. 在工作表單的 [主旨]  欄位中，輸入「相依工作」  。

4. 在功能 **區的 [工作]** 索引標籤上，按一下 [ **動作** ] 群組中的 [ **儲存] & 關閉**]。

5. 在 Outlook 的 [常用]  索引標籤上，依序按一下 [新項目] 、[其他項目] 和 [選擇表單] 。

6. 在 [選擇表單]  對話方塊中，按一下 **TaskFormRegion**，然後按一下 [開啟] 。

     **TaskFormRegion** 表單區域隨即出現。 這個表單會取代整個工作表單。 以 [工作] 資料夾中的其他工作，填入 [選取要加入相依工作清單的工作]  下拉式方塊。

7. 在工作表單的 [主旨]  欄位中，輸入「主要工作」 。

8. 在 [選取要加入相依工作清單的工作]  下拉式方塊中，選取 [相依工作] ，然後按一下 [加入相依工作] 。

     [完成率 - 相依工作] 隨即出現在 [這項工作相依於下列工作]  清單方塊中。 如此即示範您已成功處理按鈕的 `Microsoft.Office.Interop.Outlook.OlkCommandButton.Click` 事件。

9. 儲存並關閉 [主要工作]  項目。

10. 在 Outlook 中重新開啟 [相依工作] 項目。

11. 在 [相依工作] 表單中，將 [完成率]  欄位變更為 [50%] 。

12. 在 [相依 **工作] 功能** 區的 [工作] 索引標籤上，按一下 [ **動作** ] 群組中的 [ **儲存 & 關閉**]。

13. 在 Outlook 中重新開啟 [主要工作]  項目。

     [完成 50% - 相依工作] 現在會出現在 [這項工作相依於下列工作]  清單方塊中。

## <a name="next-steps"></a>後續步驟
 從這些主題，您可以進一步了解如何自訂 Outlook 應用程式的 UI：

- 若要深入瞭解如何藉由將 managed 控制項拖曳至視覺化設計工具來設計表單區域的外觀，請參閱 [逐步解說：設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)。

- 若要瞭解如何自訂 Outlook 專案的功能區，請參閱 [自訂 outlook 功能區](../vsto/customizing-a-ribbon-for-outlook.md)。

- 若要深入瞭解如何將自訂工作窗格加入 Outlook，請參閱 [自訂工作窗格](../vsto/custom-task-panes.md)。

## <a name="see-also"></a>另請參閱
- [在執行時間存取表單區域](../vsto/accessing-a-form-region-at-run-time.md)
- [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)
- [建立 Outlook 表單區域的指導方針](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [逐步解說：設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [如何：在 Outlook 增益集專案中加入表單區域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [將表單區域與 Outlook 訊息類別產生關聯](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Outlook 表單區域中的自訂動作](../vsto/custom-actions-in-outlook-form-regions.md)
- [如何：防止 Outlook 顯示表單區域](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
