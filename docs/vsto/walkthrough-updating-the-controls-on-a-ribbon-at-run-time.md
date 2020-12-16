---
title: 逐步解說：在執行時間更新功能區上的控制項
description: 瞭解如何使用功能區物件模型，在功能區載入至 Office 應用程式之後，更新功能區上的控制項。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- updating Ribbon controls
- Ribbon [Office development in Visual Studio], dynamic menu
- dynamic menus [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], updating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2246dcdca1e754c885dd610f98986306a256228c
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526046"
---
# <a name="walkthrough-update-the-controls-on-a-ribbon-at-run-time"></a>逐步解說：在執行時間更新功能區上的控制項

本逐步解說示範如何使用功能區物件模型，在功能區載入至 Office 應用程式之後，更新功能區上的控制項。

[!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

此範例會提取 Northwind 範例資料庫的資料，填入 Microsoft Office Outlook 中的下拉式方塊和功能表。 您在這些控制項中選取的專案，會自動填入電子郵件 **訊息中的** 欄位，**例如和。**

本逐步解說將說明下列工作：

- 建立新的 Outlook VSTO 增益集專案。

- 設計自訂功能區群組。

- 將自訂群組加入至內建索引標籤。

- 在執行時間更新功能區上的控制項。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件

您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Outlook

## <a name="create-a-new-outlook-vsto-add-in-project"></a>建立新的 Outlook VSTO 增益集專案

首先，建立 Outlook VSTO 增益集專案。

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>建立新的 Outlook VSTO 增益集專案

1. 在中 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，建立名稱為 **Ribbon_Update_At_Runtime** 的 Outlook VSTO 增益集專案。

2. 在 [新增專案]  對話方塊中，選取 [為方案建立目錄] 。

3. 將專案儲存至預設的專案目錄。

     如需詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

## <a name="design-a-custom-ribbon-group"></a>設計自訂功能區群組

當使用者撰寫新的郵件訊息時，就會顯示此範例的功能區。 若要建立功能區的自訂群組，請先將功能區專案加入至您的專案，然後在功能區設計工具中設計該群組。 此自訂群組將協助您從資料庫提取名稱和訂單記錄，以產生後續的電子郵件訊息給客戶。

### <a name="to-design-a-custom-group"></a>設計自訂群組

1. 在 [專案] 功能表上，按一下 [加入新項目]。

2. 選取 [ **加入新項目** ] 對話方塊中的 [ **功能區 (視覺化設計工具)**]。

3. 將新功能區的名稱變更為 **CustomerRibbon**，然後按一下 [ **新增**]。

     *CustomerRibbon.cs* 或 *CustomerRibbon .vb* 檔會在功能區設計工具中開啟，並顯示預設索引標籤和群組。

4. 按一下選取功能區設計工具。

5. 在 [**屬性**] 視窗中，按一下 [ **RibbonType** ] 屬性旁的下拉箭號，**然後按一下 [編輯]。**

     當使用者在 Outlook 中撰寫新的郵件訊息時，就會出現功能區。

6. 在功能區設計工具中，按一下 [ **Group1** ] 加以選取。

7. 在 [ **屬性** ] 視窗中，將 [ **標籤** ] 設定為 [ **客戶購買**]。

8. 從 [**工具箱**] 的 [ **Office 功能區控制項**] 索引標籤，將 **ComboBox** 拖曳至 [**客戶購買**] 群組。

9. 按一下 [ **ComboBox1** ] 加以選取。

10. 在 [ **屬性** ] 視窗中，將 **標籤** 設定為 [ **客戶**]。

11. 從 [**工具箱**] 的 [ **Office 功能區控制項**] 索引標籤中，將 **功能表** 拖曳至 [**客戶購買**] 群組。

12. 在 [ **屬性** ] 視窗中，將 [ **標籤** ] 設定為 **購買的產品**。

13. 將 **動態** 設定為 **true**。

     這可讓您在功能區載入至 Office 應用程式之後，于執行時間加入和移除功能表上的控制項。

## <a name="add-the-custom-group-to-a-built-in-tab"></a>將自訂群組新增至內建索引標籤

內建索引標籤是一個索引標籤，它已經在 Outlook Explorer 或 Inspector 的功能區上。 在這個程序中，您要將自訂群組加入內建索引標籤，然後指定自訂群組在索引標籤上的位置。

### <a name="to-add-the-custom-group-to-a-built-in-tab"></a>將自訂群組加入內建索引標籤

1. 按一下 **[tabaddins (內建的)** ] 索引標籤加以選取。

2. 在 [ **屬性** ] 視窗中，展開 [ **ControlId** ] 屬性，然後將 [ **OfficeId** ] 設定為 [ **[tabnewmailmessage]**]。

     這會將 [ **客戶購買** ] 群組新增至出現在新郵件訊息之功能區的 [ **訊息** ] 索引標籤中。

3. 按一下 [ **客戶購買** ] 群組以選取它。

4. 在 [ **屬性** ] 視窗中，展開 [ **位置** ] 屬性，然後按一下 [ **positiontype]** ] 屬性旁邊的下拉箭號，再按一下 [ **BeforeOfficeId**]。

5. 將 **OfficeId** 屬性設定為 **GroupClipboard**。

     這會將 **客戶購買** 的群組放置在 [**訊息**] 索引標籤的 [**剪貼** 簿] 群組之前。

## <a name="create-the-data-source"></a>建立資料來源

使用 [ **資料來源** ] 視窗將型別資料集加入專案。

### <a name="to-create-the-data-source"></a>若要建立資料來源

1. 在 [ **資料** ] 功能表上，請按一下 [ **加入新資料來源**]。

     這會啟動 [ **資料來源設定]**。

2. 選取 [ **資料庫**]，然後按 **[下一步]**。

3. 選取 [ **資料集**]，然後按 **[下一步]**。

4. 選取與 Northwind 範例 Microsoft SQL Server Compact 4.0 資料庫的資料連線，或使用 [ **新增連接** ] 按鈕來加入新的連接。

5. 選取或建立連接之後，請按 **[下一步]**。

6. 按 **[下一步]** 儲存連接字串。

7. 在 [ **選擇您的資料庫物件** ] 頁面上，展開 [ **資料表]**。

8. 選取下列每個資料表旁的核取方塊：

    1. **客戶**

    2. **訂單詳細資料**

    3. **訂單**

    4. **產品**

9. 按一下 [完成] 。

## <a name="update-controls-in-the-custom-group-at-run-time"></a>在執行時間更新自訂群組中的控制項

使用功能區物件模型執行下列工作：

- 將客戶名稱加入至 [ **客戶** ] 下拉式方塊。

- 將 [功能表] 和 [按鈕] 控制項加入至 [ **購買的產品** ] 功能表中，表示銷售訂單和銷售的產品。

- 使用 [ **客戶** ] 下拉式方塊和 [ **購買的產品** ] 功能表中的資料，填入新郵件的 [寄件者]、[主旨] 和 [主體] 欄位。

### <a name="to-update-controls-in-the-custom-group-by-using-the-ribbon-object-model"></a>使用功能區物件模型更新自訂群組中的控制項

1. 在 [專案] 功能表上，按一下 [加入參考]。

2. 在 [ **加入參考** ] 對話方塊中，按一下 [ **.net** ] 索引標籤，選取 [ **system.object** ] 元件，然後按一下 **[確定]**。

    這個組件包含使用 Language-Integrated Queries (LINQ) 的類別。 您會使用 LINQ，以 Northwind 資料庫的資料填入自訂群組中的控制項。

3. 在 **方案總管** 中，按一下 [ **CustomerRibbon.cs** ] 或 [ **CustomerRibbon** ] 以選取它。

4. 在 [檢視] 功能表中，按一下 [程式碼]。

    功能區程式碼檔案隨即在程式碼編輯器中開啟。

5. 在功能區程式碼檔的頂端加入下列陳述式。 這些陳述式可讓您輕鬆存取 LINQ 命名空間和 Outlook 主要 interop 組件 (PIA) 的命名空間。

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#1)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#1)]

6. 在類別內新增下列程式碼 `CustomerRibbon` 。 這個程式碼會宣告資料表和資料表配接器，您會用它們儲存來自 Northwind 資料庫之客戶、訂單、訂單詳細資料和產品資料表的資訊。

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#2)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#2)]

7. 在 `CustomerRibbon` 類別中加入下列程式碼區塊。 此程式碼會加入三個 helper 方法，以在執行時間建立功能區的控制項。

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#3)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#3)]

8. 以下列程式碼取代 `CustomerRibbon_Load` 事件處理常式方法。 這個程式碼使用 LINQ 查詢執行下列工作：

   - 使用 Northwind 資料庫中20位客戶的識別碼和名稱填入 [ **客戶** ] 下拉式方塊。

   - 呼叫 `PopulateSalesOrderInfo` helper 方法。 這個方法會使用與目前選取之客戶相關的銷售訂單號碼來更新 [ **ProductsPurchased** ] 功能表。

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#4)]

9. 將下列程式碼新增至 `CustomerRibbon` 類別。 這個程式碼使用 LINQ 查詢執行下列工作：

   - 將子功能表加入至與所選客戶相關的每個銷售訂單的 [ **ProductsPurchased** ] 功能表。

   - 在與銷售訂單相關之產品的每個子功能表加入按鈕。

   - 在每個按鈕加入事件處理常式。

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#6)]

10. 在 **方案總管** 中，按兩下功能區程式碼檔案。

     螢幕設計工具隨即開啟。

11. 在功能區設計工具中，按兩下 [ **客戶** ] 下拉式方塊。

     功能區程式碼檔案會在程式碼編輯器中開啟，且 `ComboBox1_TextChanged` 事件處理常式隨即出現。

12. 以下列程式碼取代 `ComboBox1_TextChanged` 事件處理常式。 此程式碼會執行下列工作：

    - 呼叫 `PopulateSalesOrderInfo` helper 方法。 這個方法會使用與所選客戶相關的銷售訂單來更新 [ **購買的產品** ] 功能表。

    - 呼叫 `PopulateMailItem` helper 方法，並在目前的文字，也就是選取的客戶名稱中傳遞。 這個方法會填入新郵件郵件的 [寄件者]、[主旨] 和 [主體] 欄位。

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#5)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#5)]

13. 將下列 `Click` 事件處理常式加入 `CustomerRibbon` 類別。 這段程式碼會將選取的產品名稱加入新郵件郵件的 [內文] 欄位中。

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#8)]

14. 將下列程式碼新增至 `CustomerRibbon` 類別。 此程式碼會執行下列工作：

    - 使用目前選取之客戶的電子郵件地址，填入新郵件的 [到] 行。

    - 將文字新增至新郵件郵件的 [主旨] 和 [主體] 欄位。

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#7)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#7)]

## <a name="test-the-controls-in-the-custom-group"></a>測試自訂群組中的控制項

當您在 Outlook 中開啟新的郵件表單時，會在功能區的 [**訊息**] 索引標籤上顯示名為 **客戶購買** 的自訂群組。

若要建立客戶追蹤電子郵件訊息，請選取客戶，然後選取客戶所購買的產品。 **客戶購買** 群組中的控制項會在執行時間使用 Northwind 資料庫的資料進行更新。

### <a name="to-test-the-controls-in-the-custom-group"></a>測試自訂群組中的控制項

1. 按 **F5** 執行您的專案。

     Outlook 啟動。

2. 在 Outlook **的 [檔案** ] 功能表上，指向 [ **新增**]，然後按一下 [ **郵件訊息**]。

     此時會進行下列動作：

    - 新的郵件偵測器視窗出現。

    - 在功能區的 [ **訊息** ] 索引標籤上，[ **客戶購買** ] 群組會顯示在 [ **剪貼** 簿] 群組之前。

    - 群組中的 [ **客戶** ] 下拉式方塊會以 Northwind 資料庫中的客戶名稱進行更新。

3. 在功能區的 [ **訊息** ] 索引標籤上，于 [ **客戶購買** ] 群組中，從 [ **客戶** ] 下拉式方塊中選取客戶。

     此時會進行下列動作：

    - [ **購買的產品** ] 功能表會更新，以顯示所選客戶的每個銷售訂單。

    - 每個銷售訂單的子功能表都會更新以顯示該訂單中購買的產品。

    - 選取的客戶電子郵件地址會新增至郵件訊息的 [ **到** ] 行，而郵件訊息的主旨和本文會填入文字。

4. 按一下 [ **產品購買** ] 功能表，指向任何銷售訂單，然後按一下銷售訂單中的產品。

     產品名稱會加入郵件的本文。

## <a name="next-steps"></a>後續步驟

您可以透過下列主題，進一步了解自訂 Office UI 的方式：

- 將內容為主的 UI 加入至任何文件層級的自訂。 如需詳細資訊，請參閱執行 [窗格總覽](../vsto/actions-pane-overview.md)。

- 展開標準或自訂的 Microsoft Office Outlook 表單。 如需詳細資訊，請參閱 [逐步解說：設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)。

- 將自訂工作窗格加入 Outlook。 如需詳細資訊，請參閱 [自訂工作窗格](../vsto/custom-task-panes.md)。

## <a name="see-also"></a>另請參閱

- [在執行時間存取功能區](../vsto/accessing-the-ribbon-at-run-time.md)
- [功能區總覽](../vsto/ribbon-overview.md)
- [Language-Integrated Query (LINQ)](/dotnet/csharp/linq/index)
- [如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [功能區設計工具](../vsto/ribbon-designer.md)
- [逐步解說：使用功能區設計工具建立自訂索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [功能區物件模型總覽](../vsto/ribbon-object-model-overview.md)
- [自訂 Outlook 的功能區](../vsto/customizing-a-ribbon-for-outlook.md)
- [如何：變更功能區上的索引標籤位置](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [如何：自訂內建索引標籤](../vsto/how-to-customize-a-built-in-tab.md)
- [如何：將控制項加入至 Backstage 檢視](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [如何：將功能區設計工具的功能區匯出至功能區 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [如何：顯示增益集使用者介面錯誤](../vsto/how-to-show-add-in-user-interface-errors.md)