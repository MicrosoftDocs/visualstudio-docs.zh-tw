---
title: "逐步解說： 使用內容控制項建立範本 |Microsoft 文件"
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
- building blocks [Office development in Visual Studio]
- Word [Office development in Visual Studio], creating documents
- content controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6d221b9374bf71df3d66400289c50310263c2e9e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-template-by-using-content-controls"></a>逐步解說：使用內容控制項建立範本
  本逐步解說示範如何建立文件層級自訂，這個自訂會使用內容控制項在 Microsoft Office Word 範本中建立可重複使用的結構化內容。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Word 可讓您建立一組可重複使用的文件組件，名為*建置組塊*。 這個逐步解說顯示如何建立兩個資料表做為建置組塊。 每個資料表包含數個內容控制項，可以有不同的內容類型，例如純文字或日期。 其中一個資料表包含員工的資訊，另一個資料表則包含客戶回函。  
  
 從範本建立文件之後，您可以將任一個資料表加入至文件，方法是使用數個 <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> 物件，這些物件會顯示範本中可用的建置組塊。  
  
 這個逐步解說將說明下列工作：  
  
-   在設計階段建立包含 Word 範本中內容控制項的資料表。  
  
-   以程式設計方式填入下拉式方塊內容控制項和下拉式清單內容控制項。  
  
-   防止使用者編輯指定的資料表。  
  
-   將資料表加入範本的建置組塊集合。  
  
-   建立會顯示範本中可用建置組塊的內容控制項。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="creating-a-new-word-template-project"></a>建立新的 Word 範本專案  
 建立 Word 範本，讓使用者可以輕鬆建立自己的複本。  
  
#### <a name="to-create-a-new-word-template-project"></a>建立新的 Word 範本專案  
  
1.  Word 範本專案建立名稱**MyBuildingBlockTemplate**。 在精靈中，於方案中建立新文件。 如需詳細資訊，請參閱 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]在設計工具中開啟新的 Word 範本，並將**MyBuildingBlockTemplate**專案加入**方案總管 中**。  
  
## <a name="creating-the-employee-table"></a>建立員工資料表  
 建立含有四種不同內容控制項的資料表，使用者可以在這個資料表中輸入員工資訊。  
  
#### <a name="to-create-the-employee-table"></a>建立員工資料表  
  
1.  在裝載的 Word 範本[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]設計工具中的，在功能區中，按一下**插入** 索引標籤。  
  
2.  在**資料表**群組中，按一下**資料表**，然後插入具有 2 個資料行和 4 個資料列的資料表。  
  
3.  在第一個資料行中輸入文字，讓它類似下面資料行：  
  
    ||  
    |-|  
    |**員工名稱**|  
    |**雇用日期**|  
    |**標題**|  
    |**圖片**|  
  
4.  按一下第二個資料行中第一個資料格中 (旁**員工姓名**)。  
  
5.  按一下 [功能區] 上的 [開發人員]  索引標籤。  
  
    > [!NOTE]  
    >  如果 [開發人員]  索引標籤沒有顯示，您必須先使其顯示。 如需詳細資訊，請參閱 [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)。  
  
6.  在**控制項**群組中，按一下**文字**按鈕![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl")新增<xref:Microsoft.Office.Tools.Word.PlainTextContentControl>第一個資料格中。  
  
7.  按一下第二個資料行中的第二個資料格 (旁**雇用日期**)。  
  
8.  在**控制項**群組中，按一下**日期選擇器**按鈕![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl")新增<xref:Microsoft.Office.Tools.Word.DatePickerContentControl>到第二個資料格。  
  
9. 按一下第二個資料行中的第三個資料格 (旁**標題**)。  
  
10. 在**控制項**群組中，按一下**下拉式方塊**按鈕![ComboBoxContentControl](../vsto/media/combobox.gif "ComboBoxContentControl")新增<xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>到第三個資料格。  
  
11. 按一下第二個資料行中的最後一個資料格 (旁**圖片**)。  
  
12. 在**控制項**群組中，按一下**圖片內容控制項**按鈕![PictureContentControl](../vsto/media/pictcontentcontrol.gif "PictureContentControl")新增<xref:Microsoft.Office.Tools.Word.PictureContentControl>最後一個儲存格。  
  
## <a name="creating-the-customer-feedback-table"></a>建立客戶回函資料表  
 建立含有三種不同內容控制項類型的資料表，使用者可以在這個資料表中輸入客戶回函資訊。  
  
#### <a name="to-create-the-customer-feedback-table"></a>建立客戶回函資料表  
  
1.  在 Word 範本中，按一下您稍早加入之員工資料表的後面一行，然後按下 ENTER 鍵加入新段落。  
  
2.  在功能區中，按一下 [**插入**] 索引標籤。  
  
3.  在**資料表**群組中，按一下**資料表**，然後插入具有 2 個資料行和 3 個資料列的資料表。  
  
4.  在第一個資料行中輸入文字，讓它類似下面資料行：  
  
    ||  
    |-|  
    |**客戶名稱**|  
    |**滿意度評等**|  
    |**註解**|  
  
5.  按一下第二個資料行的第一個資料格中 (旁**客戶名稱**)。  
  
6.  按一下 [功能區] 上的 [開發人員]  索引標籤。  
  
7.  在**控制項**群組中，按一下**文字**按鈕![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl")新增<xref:Microsoft.Office.Tools.Word.PlainTextContentControl>第一個資料格中。  
  
8.  按一下第二個資料行的第二個儲存格 (旁**滿意度評等**)。  
  
9. 在**控制項**群組中，按一下**下拉式選單**按鈕![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl")新增<xref:Microsoft.Office.Tools.Word.DropDownListContentControl>到第二個資料格。  
  
10. 按一下第二個資料行的最後一個儲存格 (旁**註解**)。  
  
11. 在**控制項**群組中，按一下**Rtf**按鈕![RichTextContentControl](../vsto/media/richtextcontrol.gif "RichTextContentControl")新增<xref:Microsoft.Office.Tools.Word.RichTextContentControl>最後一個儲存格。  
  
## <a name="populating-the-combo-box-and-drop-down-list-programmatically"></a>以程式設計方式填入下拉式方塊和下拉式清單  
 您可以在設計階段初始化內容控制項使用**屬性**視窗[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 也可以在執行階段再進行初始化，這樣可讓您動態設定其初始狀態。 這個逐步解說中，使用程式碼中的將項目填入<xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>和<xref:Microsoft.Office.Tools.Word.DropDownListContentControl>在執行階段，讓您可以查看這些物件運作的方式。  
  
#### <a name="to-modify-the-ui-of-the-content-controls-programmatically"></a>以程式設計方式修改內容控制項的 UI  
  
1.  在**方案總管] 中**，以滑鼠右鍵按一下**ThisDocument.cs**或**ThisDocument.vb**，然後按一下 [**檢視程式碼**。  
  
2.  將下列程式碼加入 `ThisDocument` 類別。 這個程式碼會宣告數個物件，您稍後於此逐步解說中會用到。  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#1)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#1)]  
  
3.  將下面程式碼加入 `ThisDocument` 類別的 `ThisDocument_Startup` 方法。 此程式碼會將項目加入資料表中的 <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> 和 <xref:Microsoft.Office.Tools.Word.DropDownListContentControl>，然後設定預留位置文字，在使用者編輯這些控制項之前先行顯示在控制項中。  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#2)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#2)]  
  
## <a name="preventing-users-from-editing-the-employee-table"></a>防止使用者編輯員工資料表  
 使用您稍早宣告的 <xref:Microsoft.Office.Tools.Word.GroupContentControl> 物件可保護員工資料表。 保護資料表之後，使用者仍然可以編輯資料表中的內容控制項。 但是，無法編輯第一欄中的文字或以其他方式修改資料表，例如加入或刪除資料列和資料行。 如需有關如何使用<xref:Microsoft.Office.Tools.Word.GroupContentControl>來保護文件的一部分，請參閱[內容控制項](../vsto/content-controls.md)。  
  
#### <a name="to-prevent-users-from-editing-the-employee-table"></a>防止使用者編輯員工資料表  
  
1.  請將下列程式碼加入 `ThisDocument` 類別的 `ThisDocument_Startup` 方法，在您於上一個步驟中所加入的程式碼之後。 此程式碼會將資料表放到您稍早宣告的 <xref:Microsoft.Office.Tools.Word.GroupContentControl> 物件內，藉以防止使用者編輯員工資料表。  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#3)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#3)]  
  
## <a name="adding-the-tables-to-the-building-block-collection"></a>將資料表加入至建置組塊集合  
 將資料表加入至範本中文件建置組塊的集合，以便使用者可以將您建立的資料表插入至文件。 如需文件建置組塊的詳細資訊，請參閱[內容控制項](../vsto/content-controls.md)。  
  
#### <a name="to-add-the-tables-to-the-building-blocks-in-the-template"></a>將資料表加入至範本中的建置組塊  
  
1.  請將下列程式碼加入至 `ThisDocument` 類別的 `ThisDocument_Startup` 方法，在您於上一個步驟中所加入的程式碼之後。 這個程式碼會加入包含要 Microsoft.Office.Interop.Word.BuildingBlockEntries 集合，其中包含所有可重複使用的建置組塊範本中的資料表的新建置組塊。 名為新的類別中定義新的建置組塊**Employee and Customer Information** ，系統會指派建置組塊類型 Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1。  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#4)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#4)]  
  
2.  請將下列程式碼加入至 `ThisDocument` 類別的 `ThisDocument_Startup` 方法，在您於上一個步驟中所加入的程式碼之後。 此程式碼會從範本刪除資料表。 因為您已將資料表加入至範本中可重複使用的建置組塊庫，所以不再需要它們了。 程式碼會先讓文件進入設計模式，如此就可以刪除受保護的員工資料表。  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#5)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#5)]  
  
## <a name="creating-a-content-control-that-displays-the-building-blocks"></a>建立會顯示建置組塊的內容控制項  
 建立內容控制項，用來存取您稍早建立的建置組塊 (亦即資料表)。 使用者可以按一下此控制項，將資料表加入文件。  
  
#### <a name="to-create-a-content-control-that-displays-the-building-blocks"></a>建立會顯示建置組塊的內容控制項  
  
1.  請將下列程式碼加入至 `ThisDocument` 類別的 `ThisDocument_Startup` 方法，在您於上一個步驟中所加入的程式碼之後。 此程式碼會初始化您稍早宣告的 <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> 物件。 <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>會顯示所有類別目錄中所定義的建置組塊**Employee and Customer Information**且具有建置組塊類型 Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1。  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#6)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#6)]  
  
## <a name="testing-the-project"></a>測試專案  
 使用者可以按一下文件中的建置組塊庫控制項，插入員工資料表或客戶回函資料表。 使用者可以在這兩個資料表的內容控制項中輸入或選取回應。 使用者可以修改客戶回函資料表的其他部分，但是應該無法修改員工資料表的其他部分。  
  
#### <a name="to-test-the-employee-table"></a>測試員工資料表  
  
1.  按 F5 執行專案。  
  
2.  按一下**選擇第一個的建置組塊**顯示第一個的建置組塊庫內容控制項。  
  
3.  按一下下拉箭號旁**自訂圖庫 1**標題在控制項中，並選取**Employee 資料表**。  
  
4.  按一下右邊的儲存格**員工姓名**資料格，然後輸入的名稱。  
  
     驗證您是否只能將文字加入此儲存格。 <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> 只允許使用者加入文字，不允許其他類型的內容，例如圖片或資料表。  
  
5.  按一下右邊的儲存格**雇用日期**資料格，然後在 日期選擇器中選取日期。  
  
6.  按一下右邊的儲存格**標題**資料格，然後在下拉式方塊中選取其中一個工作職稱。  
  
     (選擇性) 輸入不在清單中的工作職稱。 這是可行的，因為 <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> 可以讓使用者從項目清單中選取或自行輸入。  
  
7.  按一下右邊的儲存格的圖示**圖片**資料格，然後瀏覽至要顯示的影像。  
  
8.  嘗試將資料列或資料行加入資料表，並嘗試從資料表刪除資料列和資料行。 驗證您是否無法修改資料表。 <xref:Microsoft.Office.Tools.Word.GroupContentControl> 會防止您進行任何修改。  
  
#### <a name="to-test-the-customer-feedback-table"></a>測試客戶回函資料表  
  
1.  按一下**選擇第二個的建置組塊**顯示第二個建置組塊庫內容控制項。  
  
2.  按一下下拉箭號旁**自訂圖庫 1**標題在控制項中，並選取**Customer 資料表**。  
  
3.  按一下右邊的儲存格**客戶名稱**資料格，然後輸入的名稱。  
  
4.  按一下右邊的儲存格**滿意度評等**資料格，然後選取其中一個可用的選項。  
  
     驗證您是否無法輸入自己的項目。 <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> 只允許使用者從項目清單中選取。  
  
5.  按一下右邊的儲存格**註解**資料格，然後輸入一些註解。  
  
     (選擇性) 加入文字以外的內容，例如圖片或內嵌資料表。 這是可行的，因為 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 可以讓使用者加入文字以外的內容。  
  
6.  驗證您是否可以將資料列或資料行加入資料表，以及是否可以從資料表刪除資料列和資料行。 這是可行的，因為您尚未將資料表放入 <xref:Microsoft.Office.Tools.Word.GroupContentControl> 進行保護。  
  
7.  關閉範本。  
  
## <a name="next-steps"></a>後續步驟  
 您可以透過下列主題，進一步了解如何使用內容控制項：  
  
-   將內容控制項繫結至內嵌於文件的 XML 片段，也稱為自訂 XML 組件。 如需詳細資訊，請參閱[逐步解說： 內容控制項繫結至自訂 XML 組件](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)。  
  
## <a name="see-also"></a>請參閱  
 [使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)   
 [內容控制項](../vsto/content-controls.md)   
 [如何： 將內容控制項加入 Word 文件](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [如何： 使用內容控制項保護文件的組件](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  