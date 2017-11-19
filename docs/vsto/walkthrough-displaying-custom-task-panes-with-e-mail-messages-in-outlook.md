---
title: "逐步解說： 在 Outlook 中顯示的電子郵件訊息的自訂工作窗格 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], custom task panes
- task panes [Office development in Visual Studio], displaying with e-mail messages
- displaying custom task panes in e-mail
- e-mail [Office development in Visual Studio], custom task panes displayed in
- custom task panes [Office development in Visual Studio], displaying with e-mail messages
ms.assetid: 04943967-a7ef-4876-9584-84ada427e3f3
caps.latest.revision: "59"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b788a66eb95db5e46464048e134ab803d273d1ce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook"></a>逐步解說：在 Outlook 中的電子郵件訊息顯示自訂工作窗格
  本逐步解說示範如何針對每則已建立或開啟的電子郵件訊息，顯示唯一的自訂工作窗格執行個體。 使用者可以使用每則電子郵件訊息功能區上的按鈕，顯示或隱藏自訂工作窗格。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 若要顯示含有多個檔案總管或偵測器視窗的自訂工作窗格，您必須針對每一個開啟的視窗，建立該自訂工作窗格的執行個體。 自訂工作窗格，Outlook 視窗中的行為的詳細資訊，請參閱[自訂工作窗格](../vsto/custom-task-panes.md)。  
  
> [!NOTE]  
>  本逐步解說會呈現一小部分的 VSTO 增益集程式碼，以便更容易討論程式碼背後的邏輯。  
  
 這個逐步解說將說明下列工作：  
  
-   設計自訂工作窗格的使用者介面 (UI)。  
  
-   建立自訂功能區 UI。  
  
-   顯示含有電子郵件訊息的自訂功能區 UI。  
  
-   建立類別以管理偵測器視窗和自訂工作窗格。  
  
-   初始化和清除 VSTO 增益集所使用的資源。  
  
-   同步處理功能區切換按鈕和自訂工作窗格。  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] 或 Microsoft Outlook 2010。  
  
 ![影片連結](../vsto/media/playvideo.gif "影片連結")相關的影片示範，請參閱[如何： 使用工作窗格在 Outlook 中？](http://go.microsoft.com/fwlink/?LinkID=130309)。  
  
## <a name="creating-the-project"></a>建立專案  
 自訂工作窗格會在 VSTO 增益集中實作。請從建立 Outlook 的 VSTO 增益集專案開始。  
  
#### <a name="to-create-a-new-project"></a>若要建立新的專案  
  
1.  建立名為 **OutlookMailItemTaskPane** 的 [Outlook 增益集] 專案。 使用 [Outlook 增益集]  專案範本。 如需詳細資訊，請參閱 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會開啟 **ThisAddIn.cs** 或 **ThisAddIn.vb** 程式碼檔，並將 [OutlookMailItemTaskPane]  專案加入 [方案總管] 。  
  
## <a name="designing-the-user-interface-of-the-custom-task-pane"></a>設計自訂工作窗格的使用者介面  
 自訂工作窗格沒有視覺化設計工具，但您可以透過 UI 來設計所需的使用者控制項。 這個 VSTO 增益集中的自訂工作窗格具有內含 <xref:System.Windows.Forms.TextBox> 控制項的簡單 UI。 稍後在本逐步解說中，您會將使用者控制項加入自訂工作窗格。  
  
#### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>設計自訂工作窗格的使用者介面  
  
1.  在 [方案總管] 中，按一下 [OutlookMailItemTaskPane]  專案。  
  
2.  在 [專案]  功能表上，按一下 [加入使用者控制項] 。  
  
3.  在 [加入新項目]  對話方塊中，將使用者控制項的名稱變更為 **TaskPaneControl**，然後按一下 [加入] 。  
  
     使用者控制項隨即在設計工具中開啟。  
  
4.  從 [工具箱]  的 [通用控制項] 索引標籤，將 **TextBox** 控制項拖曳至使用者控制項。  
  
## <a name="designing-the-user-interface-of-the-ribbon"></a>設計功能區的使用者介面  
 這個 VSTO 增益集的其中一個目標就是讓使用者可以從每則電子郵件訊息的功能區，隱藏或顯示自訂工作窗格。 若要提供使用者介面，請建立顯示切換按鈕的自訂功能區 UI，使用者可按一下該切換按鈕以顯示或隱藏自訂工作窗格。  
  
#### <a name="to-create-a-custom-ribbon-ui"></a>建立自訂功能區 UI  
  
1.  在 [專案]  功能表中，按一下 [加入新項目] 。  
  
2.  選取 [ **加入新項目** ] 對話方塊中的 [ **功能區 (視覺化設計工具)**]。  
  
3.  將新功能區的名稱變更為 **ManageTaskPaneRibbon**，然後按一下 [加入] 。  
  
     **ManageTaskPaneRibbon.cs** 或 **ManageTaskPaneRibbon.vb** 檔案會在功能區設計工具中開啟，並顯示預設的索引標籤和群組。  
  
4.  在功能區設計工具中，按一下 [group1] 。  
  
5.  在 [屬性]  視窗中，將 [標籤]  屬性設定為「工作窗格管理員」 。  
  
6.  從 [工具箱]  的 [Office 功能區控制項] 索引標籤，將 ToggleButton 控制項拖曳至 [工作窗格管理員]  群組。  
  
7.  按一下 [toggleButton1] 。  
  
8.  在 [屬性]  視窗中，將 [標籤]  屬性設定為「顯示工作窗格」 。  
  
## <a name="display-the-custom-ribbon-user-interface-with-e-mail-messages"></a>顯示含有電子郵件訊息的自訂功能區使用者介面  
 您在本逐步解說中建立的自訂工作窗格，會設計為僅與含有電子郵件訊息的偵測器視窗一起出現。 因此，請設定屬性，僅與這些視窗一起顯示您的自訂功能區 UI。  
  
#### <a name="to-display-the-custom-ribbon-ui-with-e-mail-messages"></a>顯示含有電子郵件訊息的自訂功能區 UI  
  
1.  在功能區設計工具中，按一下 [ManageTaskPaneRibbon]  功能區。  
  
2.  在 [屬性]  視窗中，按一下 [RibbonType] 旁的下拉式清單，然後選取 [Microsoft.Outlook.Mail.Compose]  和 [Microsoft.Outlook.Mail.Read] 。  
  
## <a name="creating-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>建立類別以管理偵測器視窗和自訂工作窗格  
 在幾種情況下，VSTO增益集必須識別與特定電子郵件訊息相關聯的自訂工作窗格。 這些情況包括：  
  
-   使用者關閉電子郵件訊息時。 在這種情況下，VSTO 增益集必須移除對應的自訂工作窗格，以確保正確地清除 VSTO 增益集所使用的資源。  
  
-   使用者關閉自訂工作窗格時。 在這種情況下，VSTO 增益集必須更新電子郵件訊息功能區上的切換按鈕狀態。  
  
-   使用者按一下功能區上的切換按鈕時。 在這種情況下，VSTO 增益集必須隱藏或顯示對應的工作窗格。  
  
 若要啟用 VSTO 增益集以追蹤與每則開啟之電子郵件訊息相關聯的自訂工作窗格，請建立包裝了多組 <xref:Microsoft.Office.Interop.Outlook.Inspector> 和 <xref:Microsoft.Office.Tools.CustomTaskPane> 物件的自訂類別。 這個類別會針對每則電子郵件訊息建立新的自訂工作窗格物件，並在關閉對應的電子郵件訊息時，刪除自訂工作窗格。  
  
#### <a name="to-create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>建立類別以管理偵測器視窗和自訂工作窗格  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下 **ThisAddIn.cs** 或 **ThisAddIn.vb** 檔案，然後按一下 [檢視程式碼] 。  
  
2.  在檔案最上方加入下列陳述式。  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#2](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#2)]
     [!code-vb[Trin_OutlookMailItemTaskPane#2](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#2)]  
  
3.  將下列程式碼加入 **類別之外的** ThisAddIn.cs **或** ThisAddIn.vb `ThisAddIn` 檔案 (若為 Visual C#，則將這個程式碼加入 `OutlookMailItemTaskPane` 命名空間內)。 `InspectorWrapper` 類別會管理一組 <xref:Microsoft.Office.Interop.Outlook.Inspector> 和 <xref:Microsoft.Office.Tools.CustomTaskPane> 物件。 您會在下列步驟中完成這個類別的定義。  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#3](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#3)]
     [!code-vb[Trin_OutlookMailItemTaskPane#3](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#3)]  
  
4.  將下列建構函式加入您在上一個步驟中加入的程式碼之後。 這個建構函式會建立並初始化與所傳入 <xref:Microsoft.Office.Interop.Outlook.Inspector> 物件相關聯的新自訂工作窗格。 在 C# 中，這個建構函式也會將事件處理常式附加至 <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> 物件的 <xref:Microsoft.Office.Interop.Outlook.Inspector> 事件，以及 <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> 物件的 <xref:Microsoft.Office.Tools.CustomTaskPane> 事件。  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#4](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#4)]
     [!code-vb[Trin_OutlookMailItemTaskPane#4](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#4)]  
  
5.  將下列方法加入您在上一個步驟中加入的程式碼之後。 對於 <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> 類別內含之 <xref:Microsoft.Office.Tools.CustomTaskPane> 物件的 `InspectorWrapper` 事件而言，這個方法為其事件處理常式。 每當使用者開啟或關閉自訂工作窗格時，這個程式碼就會更新切換按鈕的狀態。  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#5](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#5)]
     [!code-vb[Trin_OutlookMailItemTaskPane#5](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#5)]  
  
6.  將下列方法加入您在上一個步驟中加入的程式碼之後。 對於含有目前電子郵件訊息之 <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> 物件的 <xref:Microsoft.Office.Interop.Outlook.Inspector> 事件而言，這個方法為其事件處理常式。 關閉電子郵件訊息之後，這個事件處理常式會釋放資源。 這個事件處理常式也會從 `CustomTaskPanes` 集合中移除目前的自訂工作窗格。 這有助於在開啟下一則電子郵件訊息時，防止自訂工作窗格有多個執行個體。  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#6](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#6)]
     [!code-vb[Trin_OutlookMailItemTaskPane#6](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#6)]  
  
7.  將下列程式碼加入您在上一個步驟中加入的程式碼之後。 稍後在本逐步解說中，您將在自訂功能區 UI 中從某個方法呼叫這個屬性，以顯示或隱藏自訂工作窗格。  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#7](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#7)]
     [!code-vb[Trin_OutlookMailItemTaskPane#7](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#7)]  
  
## <a name="initializing-and-cleaning-up-resources-used-by-the-add-in"></a>初始化和清除增益集所使用的資源  
 將程式碼加入 `ThisAddIn` 類別，以在載入 VSTO 增益集時初始化該增益集，並在卸載 VSTO 增益集時清除該增益集所使用的資源。 您可以設定 <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> 事件的事件處理常式，並將所有現有的電子郵件訊息傳遞至這個事件處理常式，以初始化 VSTO 增益集。 卸載 VSTO 增益集之後，中斷連結事件處理常式並清除 VSTO 增益集所使用的物件。  
  
#### <a name="to-initialize-and-clean-up-resources-used-by-the-vsto-add-in"></a>初始化和清除 VSTO 增益集所使用的資源  
  
1.  在 **ThisAddIn.cs** 或 **ThisAddIn.vb** 檔案中，找出 `ThisAddIn` 類別的定義。  
  
2.  將下列宣告加入至 `ThisAddIn` 類別：  
  
    -   `inspectorWrappersValue` 欄位包含 VSTO 增益集所管理的全部 <xref:Microsoft.Office.Interop.Outlook.Inspector> 和 `InspectorWrapper` 物件。  
  
    -   `inspectors` 欄位會維護目前 Outlook 執行個體中偵測器視窗的集合參考。 這個參考可以防止記憶體回收行程釋放包含 <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> 事件之事件處理常式的記憶體，您將在下一個步驟中宣告該事件。  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#8](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#8)]
     [!code-vb[Trin_OutlookMailItemTaskPane#8](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#8)]  
  
3.  以下列程式碼取代 `ThisAddIn_Startup` 方法。 這個程式碼會將事件處理常式附加至 <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> 事件，而該事件會將每一個現有的 <xref:Microsoft.Office.Interop.Outlook.Inspector> 物件傳遞至事件處理常式。 如果使用者在 Outlook 已經執行之後載入 VSTO 增益集，則 VSTO 增益集會使用這項資訊，為所有已經開啟的電子郵件訊息建立自訂工作窗格。  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#9](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#9)]
     [!code-vb[Trin_OutlookMailItemTaskPane#9](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#9)]  
  
4.  以下列程式碼取代 `ThisAddIn_ShutDown` 方法。 這個程式碼會中斷連結 <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> 事件處理常式，並清除 VSTO 增益集所使用的物件。  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#10](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#10)]
     [!code-vb[Trin_OutlookMailItemTaskPane#10](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#10)]  
  
5.  將下列 <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> 事件處理常式加入 `ThisAddIn` 類別。 如果新的 <xref:Microsoft.Office.Interop.Outlook.Inspector> 包含電子郵件訊息，此方法會建立新 `InspectorWrapper` 物件的執行個體，以管理電子郵件訊息與對應工作窗格之間的關係。  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#11](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#11)]
     [!code-vb[Trin_OutlookMailItemTaskPane#11](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#11)]  
  
6.  將下列屬性加入 `ThisAddIn` 類別。 這個屬性會將私用 `inspectorWrappersValue` 欄位公開至 `ThisAddIn` 類別外的程式碼。  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#12](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#12)]
     [!code-vb[Trin_OutlookMailItemTaskPane#12](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#12)]  
  
## <a name="checkpoint"></a>檢查點  
 建置您的專案，並確定專案在編譯時未發生任何錯誤。  
  
#### <a name="to-build-your-project"></a>建置您的專案  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下 [OutlookMailItemTaskPane]  專案，然後按一下 [建置] 。 確認專案編譯無誤。  
  
## <a name="synchronizing-the-ribbon-toggle-button-with-the-custom-task-pane"></a>同步處理功能區切換按鈕和自訂工作窗格  
 當工作窗格可見時，切換按鈕會呈現已按下狀態；當工作窗格隱藏時，切換按鈕會呈現未按下狀態。 若要同步處理按鈕和自訂工作窗格的狀態，請修改切換按鈕的 <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> 事件處理常式。  
  
#### <a name="to-synchronize-the-custom-task-pane-with-the-toggle-button"></a>同步處理自訂工作窗格和切換按鈕  
  
1.  在功能區設計工具中，按兩下 [顯示工作窗格]  切換按鈕。  
  
     Visual Studio 會自動產生名為 `toggleButton1_Click`的事件處理常式，以處理切換按鈕的 <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> 事件。 Visual Studio 也會在程式碼編輯器中開啟 **ManageTaskPaneRibbon.cs** 或 **ManageTaskPaneRibbon.vb** 檔案。  
  
2.  將下列陳述式加入 **ManageTaskPaneRibbon.cs** 或 **ManageTaskPaneRibbon.vb** 檔案的頂端。  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#14](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs#14)]
     [!code-vb[Trin_OutlookMailItemTaskPane#14](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb#14)]  
  
3.  以下列程式碼取代 `toggleButton1_Click` 事件處理常式。 當使用者按一下切換按鈕時，這個方法會隱藏或顯示與目前偵測器視窗相關聯的自訂工作窗格。  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#15](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs#15)]
     [!code-vb[Trin_OutlookMailItemTaskPane#15](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb#15)]  
  
## <a name="testing-the-project"></a>測試專案  
 當您開始偵錯專案時，會開啟 Outlook 並載入 VSTO 增益集。 VSTO 增益集會針對每則已開啟的電子郵件訊息，顯示唯一的自訂工作窗格執行個體。 建立數則新的電子郵件訊息以測試程式碼。  
  
#### <a name="to-test-the-vsto-add-in"></a>測試 VSTO 增益集  
  
1.  按 F5。  
  
2.  在 Outlook 中，按一下 [新增]  以建立新的電子郵件訊息。  
  
3.  在電子郵件訊息的功能區上，按一下 [增益集]  索引標籤，然後按一下 [顯示工作窗格]  按鈕。  
  
     確認會顯示顯示標題為 [我的工作窗格]  且內含電子郵件訊息的工作窗格。  
  
4.  在工作窗格的文字方塊中，輸入「第一個工作窗格」  。  
  
5.  關閉工作窗格。  
  
     確認 [顯示工作窗格]  按鈕的狀態會變更，而不再是已按下的狀態。  
  
6.  再按一次 [顯示工作窗格]  按鈕。  
  
     確認工作窗格會開啟，而且文字方塊仍含有「第一個工作窗格」 字串。  
  
7.  在 Outlook 中，按一下 [新增]  以建立第二則電子郵件訊息。  
  
8.  在電子郵件訊息的功能區上，按一下 [增益集]  索引標籤，然後按一下 [顯示工作窗格]  按鈕。  
  
     確認會顯示顯示標題為 [我的工作窗格]  且內含電子郵件訊息的工作窗格，而且這個工作窗格中的文字方塊是空的。  
  
9. 在工作窗格的文字方塊中，輸入「第二個工作窗格」  。  
  
10. 將焦點變更至第一則電子郵件訊息。  
  
     確認與這則電子郵件訊息相關聯的工作窗格仍在文字方塊中顯示「第一個工作窗格」  。  
  
 這個 VSTO 增益集也會處理您可以嘗試的更進階案例。 例如，您可以使用 [下一項目]  和 [前一項目]  按鈕，在檢視電子郵件時測試行為。 您也可以在卸載 VSTO 增益集、開啟數則電子郵件訊息，然後重新載入 VSTO 增益集時測試行為。  
  
## <a name="next-steps"></a>後續步驟  
 您可以透過下列主題，進一步了解如何建立自訂工作窗格：  
  
-   在 VSTO 增益集中為不同應用程式建立自訂工作窗格。 如需支援自訂工作窗格之應用程式的詳細資訊，請參閱[自訂工作窗格](../vsto/custom-task-panes.md)。  
  
-   使用自訂工作窗格自動化 Microsoft Office 應用程式。 如需詳細資訊，請參閱 [Walkthrough: Automating an Application from a Custom Task Pane](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)。  
  
-   在 Excel 中，建立可用來隱藏或顯示自訂工作窗格的功能區按鈕。 如需詳細資訊，請參閱 [Walkthrough: Synchronizing a Custom Task Pane with a Ribbon Button](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)。  
  
## <a name="see-also"></a>另請參閱  
 [自訂工作窗格](../vsto/custom-task-panes.md)   
 [如何： 應用程式中加入自訂工作窗格](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [逐步解說： 自動化從自訂工作窗格應用程式](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [逐步解說： 使用功能區按鈕同步處理自訂工作窗格](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [功能區概觀](../vsto/ribbon-overview.md)   
 [Outlook 物件模型概觀](../vsto/outlook-object-model-overview.md)   
 [在執行階段存取功能區](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  