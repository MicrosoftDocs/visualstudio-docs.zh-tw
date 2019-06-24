---
title: 將控制項加入文件在 VSTO 增益集中的執行階段
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], adding controls
- application-level add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to documents at run time
- documents [Office development in Visual Studio], adding controls at run time
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b6ac01f32a14589837d0cb7707cb3d2f8946bd0a
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328405"
---
# <a name="walkthrough-add-controls-to-a-document-at-runtime-in-a-vsto-add-in"></a>逐步解說：將控制項加入文件在執行階段中的 VSTO 增益集
  您可以使用 VSTO 增益集，將控制項加入任何開啟的 Microsoft Office Word 文件中。 本逐步解說示範如何使用功能區，讓使用者可以加入<xref:Microsoft.Office.Tools.Word.Controls.Button>或<xref:Microsoft.Office.Tools.Word.RichTextContentControl>文件。

 **適用於：** 本主題中的資訊適用於 Word 2010 的 VSTO 增益集專案。 如需詳細資訊，請參閱[依 Office 應用程式和專案類型提供的功能](../vsto/features-available-by-office-application-and-project-type.md)。

 這個逐步解說將說明下列工作：

- 建立新的 Word VSTO 增益集專案。

- 提供可將控制項加入文件的使用者介面 (UI)。

- 將控制項加入文件在執行階段。

- 移除文件的控制項。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成此逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。

## <a name="create-a-new-word-add-in-project"></a>建立新的 Word 增益集專案
 請從建立 Word VSTO 增益集專案開始。

### <a name="to-create-a-new-word-vsto-add-in-project"></a>建立新的 Word VSTO 增益集專案

1. 建立 word 的 VSTO 增益集專案名稱**WordDynamicControls**。 如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

2. 加入 **Microsoft.Office.Tools.Word.v4.0.Utilities.dll** 組件的參考。 本逐步解說稍後會需要用到此參考，以透過程式設計的方式將 Windows Forms 控制項加入文件。

## <a name="provide-a-ui-to-add-controls-to-a-document"></a>提供可將控制項加入文件的 UI
 將自訂索引標籤加入 Word 功能區。 使用者可以選取索引標籤上的核取方塊，將控制項加入文件。

### <a name="to-provide-a-ui-to-add-controls-to-a-document"></a>提供可將控制項加入文件的 UI

1. 在 [專案]  功能表中，按一下 [加入新項目]  。

2. 選取 [ **加入新項目** ] 對話方塊中的 [ **功能區 (視覺化設計工具)** ]。

3. 將新功能區的名稱變更為 **MyRibbon**，然後按一下 [加入]  。

    **MyRibbon.cs** 或 **MyRibbon.vb** 檔案會在功能區設計工具中開啟，並顯示預設索引標籤和群組。

4. 在功能區設計工具中，按一下 [group1]  群組。

5. 在 [屬性]  視窗中，將 [group1]  的 [Label]  屬性變更為 [加入控制項]  。

6. 從 [工具箱]  的 [Office 功能區控制項]  索引標籤，將 **CheckBox** 控制項拖曳至 [group1]  。

7. 按一下 [CheckBox1]  予以選取。

8. 在 [屬性]  視窗中變更下列屬性。

   | 屬性 | 值 |
   |-----------|-----------------------|
   | **名稱** | **addButtonCheckBox** |
   | **標籤** | **加入按鈕** |

9. 將第二個核取方塊加入 [group1]  ，然後變更下列屬性。

   | 屬性 | 值 |
   |-----------|---------------------------|
   | **名稱** | **addRichTextCheckBox** |
   | **Label** | **加入 RTF 控制項** |

10. 在功能區設計工具中，按兩下 [加入按鈕]  。

     在程式碼編輯器中，隨即開啟 [加入按鈕] <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click>**核取方塊的** 事件處理常式。

11. 返回功能區設計工具並按兩下 [加入 RTF 控制項]  。

     在程式碼編輯器中，隨即開啟 [加入 RTF 控制項] <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click>**核取方塊的** 事件處理常式。

    稍後在本逐步解說中，您將會把這些程式碼加入這些事件處理常式，以加入和移除使用中文件的控制項。

## <a name="add-and-remove-controls-on-the-active-document"></a>加入和移除使用中文件的控制項
 在 VSTO 增益集程式碼中，您必須將使用中文件轉換成 <xref:Microsoft.Office.Tools.Word.Document>*主項目* ，才能加入控制項。 在 Office 方案中，Managed 控制項只能加入主項目，主項目是做為控制項的容器。 在 VSTO 增益集專案中，主項目可由在執行階段使用`GetVstoObject`方法。

 將方法加入 `ThisAddIn` 類別，可以呼叫該類別來加入或移除使用中文件的 <xref:Microsoft.Office.Tools.Word.Controls.Button> 或 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 。 稍後在本逐步解說，您將從功能區上之核取方塊的 <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> 事件處理常式呼叫這些方法。

### <a name="to-add-and-remove-controls-on-the-active-document"></a>加入和移除使用中文件的控制項

1. 在 [**方案總管] 中**，按兩下*ThisAddIn.cs*或*ThisAddIn.vb*在程式碼編輯器中開啟檔案。

2. 將下列程式碼加入 `ThisAddIn` 類別。 此程式碼會宣告 <xref:Microsoft.Office.Tools.Word.Controls.Button> 和 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 物件，它們代表將會加入文件的控制項。

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#1)]

3. 將下列方法加入 `ThisAddIn` 類別。 當使用者按一下功能區上的 [加入按鈕]  核取方塊時，如果已選取核取方塊，則此方法會將 <xref:Microsoft.Office.Tools.Word.Controls.Button> 加入文件目前的選取範圍，如果已清除核取方塊則會移除 <xref:Microsoft.Office.Tools.Word.Controls.Button> 。

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#2)]

4. 將下列方法加入 `ThisAddIn` 類別。 當使用者按一下功能區上的 [加入 RTF 控制項]  核取方塊時，如果已選取核取方塊，則此方法會將 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 加入文件目前的選取範圍，如果已清除核取方塊則會移除 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 。

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#3)]

## <a name="remove-the-button-control-when-the-document-is-saved"></a>儲存文件時移除按鈕控制項
 在儲存文件然後關閉時，不會保存 Windows Forms 控制項。 不過，每個控制項的 ActiveX 包裝函式會保留在文件中，而當使用者重新開啟文件時，會看到這個包裝函式的框線。 有幾種方式可以在 VSTO 增益集中清除動態建立的 Windows Forms 控制項。在本逐步解說中，您會以程式設計方式，在儲存文件時移除 <xref:Microsoft.Office.Tools.Word.Controls.Button> 控制項。

### <a name="to-remove-the-button-control-when-the-document-is-saved"></a>儲存文件時移除按鈕控制項

1. 在  *ThisAddIn.cs*或是*ThisAddIn.vb*程式碼檔案中，將下列方法加入`ThisAddIn`類別。 這個方法是 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> 事件的事件處理常式。 如果已儲存的文件有與它相關的 <xref:Microsoft.Office.Tools.Word.Document> 主項目，事件處理常式會取得主項目並移除 <xref:Microsoft.Office.Tools.Word.Controls.Button> 控制項 (如果存在的話)。

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#4)]

2. 在 C# 中，將下列程式碼加入 `ThisAddIn_Startup` 事件處理常式。 在 C# 中連接 `Application_DocumentBeforeSave` 事件處理常式和 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> 事件時需要此程式碼。

     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#5)]

## <a name="add-and-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>加入和移除控制項，當使用者按一下功能區上的核取方塊
 最後，修改<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click>加入要新增或移除文件上的控制項的功能區的事件處理常式的核取方塊。

### <a name="to-add-or-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>若要新增或移除控制當使用者按一下功能區上的核取方塊

1. 在  *MyRibbon.cs*或*MyRibbon.vb*程式碼檔案中，將產生`addButtonCheckBox_Click`和`addRichTextCheckBox_Click`為下列程式碼的事件處理常式。 此程式碼會重新定義這些事件處理常式，呼叫您稍早在本逐步解說中加入 `ToggleButtonOnDocument` 類別的 `ToggleRichTextControlOnDocument` 和 `ThisAddIn` 方法。

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.vb#6)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.cs#6)]

## <a name="test-the-solution"></a>測試方案
 從功能區上的自訂索引標籤選取控制項，將此控制項加入文件。 當您儲存文件時，會移除 <xref:Microsoft.Office.Tools.Word.Controls.Button> 控制項。

### <a name="to-test-the-solution"></a>若要測試方案

1. 按下**F5**執行您的專案。

2. 在使用中文件中，按下**Enter**數次，以加入新的空白段落的文件。

3. 選取第一個段落。

4. 按一下 [增益集]  索引標籤。

5. 在 [加入控制項]  群組中，按一下 [加入按鈕]  。

     按鈕隨即出現在第一個段落中。

6. 選取最後一個段落。

7. 在 [加入控制項]  群組中，按一下 [加入 RTF 控制項]  。

     Rich text 格式內容控制項會加入最後一個段落。

8. 儲存文件。

     按鈕會從文件中移除。

## <a name="next-steps"></a>後續步驟
 您可以從下列主題進一步了解 VSTO 增益集的控制項：

- 如需示範如何在執行階段的文件中加入許多其他類型的控制項，並重新開啟文件時，重新建立控制項的範例，請參閱 Word 增益集動態控制項範例： [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md).

- 如需示範如何使用適用於 Excel 的 VSTO 增益集，將控制項加入工作表的逐步解說，請參閱[逐步解說：將控制項加入工作表，在 VSTO 增益集專案中的執行階段](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md)。

## <a name="see-also"></a>另請參閱
- [Word 方案](../vsto/word-solutions.md)
- [將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [保存動態控制項中的 Office 文件](../vsto/persisting-dynamic-controls-in-office-documents.md)
- [如何：將 Windows Form 控制項加入 Office 文件](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [如何：將內容控制項加入 Word 文件](../vsto/how-to-add-content-controls-to-word-documents.md)
- [擴充 Word 文件和 Excel 活頁簿，VSTO 增益集在執行階段](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
