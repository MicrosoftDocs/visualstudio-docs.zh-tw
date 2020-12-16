---
title: 逐步解說：使用內容控制項建立範本
description: 瞭解如何建立檔層級自訂，以使用內容控制項在 Microsoft Word 範本中建立結構化和可重複使用的內容。
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- building blocks [Office development in Visual Studio]
- Word [Office development in Visual Studio], creating documents
- content controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2dd7e75048a84a4e235390b99d17d48dfad039ec
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524979"
---
# <a name="walkthrough-create-a-template-by-using-content-controls"></a>逐步解說：使用內容控制項建立範本
  本逐步解說示範如何建立文件層級自訂，這個自訂會使用內容控制項在 Microsoft Office Word 範本中建立可重複使用的結構化內容。

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Word 可讓您建立可重複使用之檔元件的集合，名為 *組建區塊*。 這個逐步解說顯示如何建立兩個資料表做為建置組塊。 每個資料表包含數個內容控制項，可以有不同的內容類型，例如純文字或日期。 其中一個資料表包含員工的資訊，另一個資料表則包含客戶回函。

 從範本建立文件之後，您可以將任一個資料表加入至文件，方法是使用數個 <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> 物件，這些物件會顯示範本中可用的建置組塊。

 本逐步解說將說明下列工作：

- 在設計階段建立包含 Word 範本中內容控制項的資料表。

- 以程式設計方式填入下拉式方塊內容控制項和下拉式清單內容控制項。

- 防止使用者編輯指定的資料表。

- 將資料表加入範本的建置組塊集合。

- 建立會顯示範本中可用建置組塊的內容控制項。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-a-new-word-template-project"></a>建立新的 Word 範本專案
 建立 Word 範本，讓使用者可以輕鬆建立自己的複本。

### <a name="to-create-a-new-word-template-project"></a>建立新的 Word 範本專案

1. 建立名稱為 **MyBuildingBlockTemplate** 的單字模板專案。 在精靈中，於方案中建立新文件。 如需詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 在設計工具中開啟新的 Word 範本，並將 **MyBuildingBlockTemplate** 專案新增至 **方案總管**。

## <a name="create-the-employee-table"></a>建立 employee 資料表
 建立含有四種不同內容控制項的資料表，使用者可以在這個資料表中輸入員工資訊。

### <a name="to-create-the-employee-table"></a>建立員工資料表

1. 在設計工具所裝載的 Word 範本中 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，按一下功能區上的 [ **插入** ] 索引標籤。

2. 在 [ **資料表]** 群組中，按一下 [ **資料表**]，然後插入具有兩個數據行和四個數據列的資料表。

3. 在第一個資料行中輸入文字，讓它類似下面資料行：

   ||
   |-|
   |**員工名稱**|
   |**雇用日期**|
   |**標題**|
   |**Picture**|

4. 按一下第二個數據行中的第一個資料格 ([ **員工名稱** ]) 旁。

5. 按一下 [功能區] 上的 [開發人員]  索引標籤。

   > [!NOTE]
   > 如果 [開發人員]  索引標籤沒有顯示，您必須先使其顯示。 如需詳細資訊，請參閱 [如何：在功能區顯示開發人員](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)索引標籤。

6. 在 [ **控制項** ] 群組中，按一下 [ **文字** ] 按鈕 ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") ，將加入 <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> 至第一個儲存格。

7. 按一下第二個數據行中的第二個數據格 ([ **雇用日期** ]) 旁。

8. 在 [ **控制項** ] 群組中，按一下 [ **日期選擇器** ] 按鈕 ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") ，將加入 <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> 至第二個數據格。

9. 在 [ **標題**) ] 旁，按一下第二個數據行中的第三個數據格 (。

10. 在 [ **控制項** ] 群組中，按一下 **下拉式** 方塊按鈕 ![ComboBoxContentControl](../vsto/media/combobox.gif "ComboBoxContentControl") ，將加入 <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> 至第三個數據格。

11. 按一下 [ **圖片** ]) 旁邊 (第二個數據行中的最後一個資料格。

12. 在 [ **控制項** ] 群組中，按一下 [ **圖片內容控制項** ] 按鈕 ![PictureContentControl](../vsto/media/pictcontentcontrol.gif "PictureContentControl") ，將新增 <xref:Microsoft.Office.Tools.Word.PictureContentControl> 至最後一個儲存格。

## <a name="create-the-customer-feedback-table"></a>建立客戶意見表
 建立含有三種不同內容控制項類型的資料表，使用者可以在這個資料表中輸入客戶回函資訊。

### <a name="to-create-the-customer-feedback-table"></a>建立客戶回函資料表

1. 在 Word 範本中，按一下您稍早新增的 employee 資料表之後的那一行，然後按下 **enter** 鍵來加入新段落。

2. 在功能區上，按一下 [ **插入** ] 索引標籤。

3. 在 [ **資料表]** 群組中，按一下 [ **資料表**]，然後插入具有兩個數據行和三個數據列的資料表。

4. 在第一個資料行中輸入文字，讓它類似下面資料行：

   ||
   |-|
   |**客戶名稱**|
   |**滿意度評等**|
   |**註解**|

5. 在第二個數據行的第一個資料格中按一下 [ **客戶名稱** ]) 旁的 (。

6. 按一下 [功能區] 上的 [開發人員]  索引標籤。

7. 在 [ **控制項** ] 群組中，按一下 [ **文字** ] 按鈕 ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") ，將加入 <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> 至第一個儲存格。

8. 在第二個數據行的第二個數據格中按一下， ([ **滿意度評** 等]) 旁。

9. 在 [ **控制項** ] 群組中，按一下 **下拉式清單** 按鈕 ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") ，將加入 <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> 至第二個數據格。

10. 按一下 [ **批註** ]) 旁邊 (第二個數據行的最後一個資料格。

11. 在 [ **控制項** ] 群組中，按一下 **Rich Text** 按鈕 ![RichTextContentControl](../vsto/media/richtextcontrol.gif "RichTextContentControl") ，將加入 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 到最後一個儲存格。

## <a name="populate-the-combo-box-and-drop-down-list-programmatically"></a>以程式設計方式填入下拉式方塊和下拉式清單
 您可以使用中的 [ **屬性** ] 視窗，在設計階段初始化內容控制項 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。 也可以在執行階段再進行初始化，這樣可讓您動態設定其初始狀態。 在這個逐步解說中，使用程式碼在執行時間填入和中的專案， <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> 讓您可以查看這些物件的運作方式。

### <a name="to-modify-the-ui-of-the-content-controls-programmatically"></a>以程式設計方式修改內容控制項的 UI

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **ThisDocument.cs** ] 或 [ **ThisDocument**]，然後按一下 [ **視圖程式碼**]。

2. 將下列程式碼新增至 `ThisDocument` 類別。 這個程式碼會宣告數個物件，您稍後於此逐步解說中會用到。

     [!code-vb[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#1)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#1)]

3. 將下面程式碼加新增至 `ThisDocument` 類別的 `ThisDocument_Startup` 方法。 此程式碼會將項目加入資料表中的 <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> 和 <xref:Microsoft.Office.Tools.Word.DropDownListContentControl>，然後設定預留位置文字，在使用者編輯這些控制項之前先行顯示在控制項中。

     [!code-vb[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#2)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#2)]

## <a name="prevent-users-from-editing-the-employee-table"></a>防止使用者編輯員工資料表
 使用您稍早宣告的 <xref:Microsoft.Office.Tools.Word.GroupContentControl> 物件可保護員工資料表。 保護資料表之後，使用者仍然可以編輯資料表中的內容控制項。 但是，無法編輯第一欄中的文字或以其他方式修改資料表，例如加入或刪除資料列和資料行。 如需如何使用 <xref:Microsoft.Office.Tools.Word.GroupContentControl> 保護檔一部分的詳細資訊，請參閱 [內容控制項](../vsto/content-controls.md)。

### <a name="to-prevent-users-from-editing-the-employee-table"></a>防止使用者編輯員工資料表

1. 請將下列程式碼加入至 `ThisDocument` 類別的 `ThisDocument_Startup` 方法，在您於上一個步驟中所加入的程式碼之後。 此程式碼會將資料表放到您稍早宣告的 <xref:Microsoft.Office.Tools.Word.GroupContentControl> 物件內，藉以防止使用者編輯員工資料表。

     [!code-vb[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#3)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#3)]

## <a name="add-the-tables-to-the-building-block-collection"></a>將資料表新增至組建區塊集合
 將資料表加入至範本中文件建置組塊的集合，以便使用者可以將您建立的資料表插入至文件。 如需檔建立區塊的詳細資訊，請參閱 [內容控制項](../vsto/content-controls.md)。

### <a name="to-add-the-tables-to-the-building-blocks-in-the-template"></a>將資料表加入至範本中的建置組塊

1. 請將下列程式碼加入至 `ThisDocument` 類別的 `ThisDocument_Startup` 方法，在您於上一個步驟中所加入的程式碼之後。 此程式碼會將包含資料表的新組建區塊加入至 BuildingBlockEntries 集合，其中包含範本中所有可重複使用的組建區塊。 新的組建區塊會定義在名為 **Employee 和 Customer Information** 的新類別中，而且會被指派建立區塊類型 `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1` 。

     [!code-vb[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#4)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#4)]

2. 請將下列程式碼加入至 `ThisDocument` 類別的 `ThisDocument_Startup` 方法，在您於上一個步驟中所加入的程式碼之後。 此程式碼會從範本刪除資料表。 因為您已將資料表加入至範本中可重複使用的建置組塊庫，所以不再需要它們了。 程式碼會先讓文件進入設計模式，如此就可以刪除受保護的員工資料表。

     [!code-vb[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#5)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#5)]

## <a name="create-a-content-control-that-displays-the-building-blocks"></a>建立顯示組建區塊的內容控制項
 建立內容控制項，用來存取您稍早建立的建置組塊 (亦即資料表)。 使用者可以按一下此控制項，將資料表加入文件。

### <a name="to-create-a-content-control-that-displays-the-building-blocks"></a>建立會顯示建置組塊的內容控制項

1. 請將下列程式碼加入至 `ThisDocument` 類別的 `ThisDocument_Startup` 方法，在您於上一個步驟中所加入的程式碼之後。 此程式碼會初始化您稍早宣告的 <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> 物件。 <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>會顯示在類別目錄 **員工和客戶資訊** 中定義的所有組建區塊，以及具有建立區塊類型的組建區塊 `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1` 。

     [!code-vb[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#6)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#6)]

## <a name="test-the-project"></a>測試專案
 使用者可以按一下文件中的建置組塊庫控制項，插入員工資料表或客戶回函資料表。 使用者可以在這兩個資料表的內容控制項中輸入或選取回應。 使用者可以修改客戶回函資料表的其他部分，但是應該無法修改員工資料表的其他部分。

### <a name="to-test-the-employee-table"></a>測試員工資料表

1. 按 **F5** 執行專案。

2. 按一下 **[選擇您的第一個組建區塊** ]，以顯示第一個組建區塊資源庫內容控制項。

3. 按一下控制項中 [ **自訂圖庫 1** ] 標題旁邊的下拉式箭號，然後選取 [ **員工資料表**]。

4. 按一下 [ **員工名稱** ] 儲存格右邊的儲存格，然後輸入名稱。

     驗證您是否只能將文字加入此儲存格。 <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> 只允許使用者加入文字，不允許其他類型的內容，例如圖片或資料表。

5. 按一下 [ **雇用日期** ] 儲存格右邊的儲存格，並在日期選擇器中選取日期。

6. 按一下 [ **標題** ] 儲存格右邊的儲存格，然後選取下拉式方塊中的其中一個工作標題。

     (選擇性) 輸入不在清單中的工作職稱。 這是可行的，因為 <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> 可以讓使用者從項目清單中選取或自行輸入。

7. 按一下 [ **圖片** ] 儲存格右邊的圖示，然後流覽至影像來顯示它。

8. 嘗試將資料列或資料行加入資料表，並嘗試從資料表刪除資料列和資料行。 驗證您是否無法修改資料表。 <xref:Microsoft.Office.Tools.Word.GroupContentControl> 會防止您進行任何修改。

### <a name="to-test-the-customer-feedback-table"></a>測試客戶回函資料表

1. 按一下 **[選擇第二個組建區塊** ]，以顯示第二個組建區塊資源庫內容控制項。

2. 按一下控制項中 [ **自訂圖庫 1** ] 標題旁邊的下拉式箭號，然後選取 [ **客戶資料表**]。

3. 按一下 [ **客戶名稱** ] 儲存格右邊的儲存格，然後輸入名稱。

4. 按一下 [ **滿意度評** 等] 儲存格右邊的儲存格，然後選取其中一個可用的選項。

     驗證您是否無法輸入自己的項目。 <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> 只允許使用者從項目清單中選取。

5. 按一下 [ **批註** ] 儲存格右邊的儲存格，然後輸入一些批註。

     (選擇性) 加入文字以外的內容，例如圖片或內嵌資料表。 這是可行的，因為 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 可以讓使用者加入文字以外的內容。

6. 驗證您是否可以將資料列或資料行加入資料表，以及是否可以從資料表刪除資料列和資料行。 這是可行的，因為您尚未將資料表放入 <xref:Microsoft.Office.Tools.Word.GroupContentControl> 進行保護。

7. 關閉範本。

## <a name="next-steps"></a>後續步驟
 您可以透過下列主題，進一步了解如何使用內容控制項：

- 將內容控制項繫結至內嵌於文件的 XML 片段，也稱為自訂 XML 組件。 如需詳細資訊，請參閱 [逐步解說：將內容控制項系結至自訂 XML 元件](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)。

## <a name="see-also"></a>另請參閱
- [使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)
- [內容控制項](../vsto/content-controls.md)
- [如何：將內容控制項新增至 Word 檔](../vsto/how-to-add-content-controls-to-word-documents.md)
- [如何：使用內容控制項保護檔的元件](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
- [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [在執行時間將控制項新增至 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)
