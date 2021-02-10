---
title: 使用按鈕在檔的文字方塊中顯示文字
description: 瞭解如何在 Microsoft Word 的檔層級自訂中使用按鈕和文字方塊。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text boxes, displaying text in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0efea386da2bec0136a8a5399a04b9ce8cabf5c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942096"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-document-using-a-button"></a>逐步解說：使用按鈕在檔的文字方塊中顯示文字
  本逐步解說示範如何在 Microsoft Office Word 的文件層級自訂中使用按鈕和文字方塊。

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 本逐步解說將說明下列工作：

- 在設計階段，將控制項新增至文件層級專案中的 Word 文件。

- 按一下按鈕時填入文字方塊。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>建立專案
 第一個步驟是建立 Windows 文件專案。

### <a name="to-create-a-new-project"></a>建立新的專案

1. 使用 [ **我的單字** 名稱] 按鈕建立 word 檔專案。 在嚮導中，選取 [ **建立新檔**]。

     如需詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

     Visual Studio 會在設計工具中開啟新的 Word 檔，並將 [ **我的文字] 按鈕** 專案加入 **方案總管**。

## <a name="add-controls-to-the-word-document"></a>將控制項新增至 Word 檔
 使用者介面控制項包含 Word 文件上的一個按鈕和一個文字方塊。

### <a name="to-add-a-button-and-a-text-box"></a>新增按鈕和文字方塊

1. 請確認已在 Visual Studio 設計工具中開啟文件。

2. 從 [**工具箱**] 的 [**通用控制項**] 索引標籤，將 <xref:Microsoft.Office.Tools.Word.Controls.TextBox> 控制項拖曳至檔。

   > [!NOTE]
   > 在 Word 中，控制項預設會內嵌於文字。 您可以藉由在 Word 中 [**選項**] 對話方塊的 [**編輯**] 索引標籤上變更預設值，修改控制項和繪圖物件的插入方式。

3. 在 [檢視]  功能表上，按一下 [屬性視窗]  。

4. 在 [**屬性**] 視窗下拉式方塊中尋找 **TextBox1** ，並將文字方塊的 [**名稱**] 屬性變更 **為 [文字記錄**]。

5. 將 **按鈕** 控制項拖曳至檔，並變更下列屬性。

   |屬性|值|
   |--------------|-----------|
   |**名稱**|**insertText**|
   |**Text**|**插入文字**|

   現在，您可以撰寫在按一下按鈕時將執行的程式碼。

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>按一下按鈕時填入文字方塊
 每次使用者按一下按鈕時， **Hello World！** 會加入到文字方塊中。

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>在按一下按鈕時寫入至文字方塊

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **ThisDocument**]，然後按一下快捷方式功能表上的 [ **視圖程式碼** ]。

2. 將下列程式碼新增至按鈕的 <xref:System.Windows.Forms.Control.Click> 事件處理常式。

     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#7)]

3. 在 C# 中，您必須將按鈕的事件處理常式新增至 <xref:Microsoft.Office.Tools.Word.Document.Startup> 事件。 如需建立事件處理常式的詳細資訊，請參閱 [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#8)]

## <a name="test-the-application"></a>測試應用程式
 您現在可以測試檔案，以確保訊息 **Hello World！** 當您按一下按鈕時，會出現在文字方塊中。

### <a name="to-test-your-document"></a>測試文件

1. 按 **F5** 執行您的專案。

2. 按一下按鈕。

3. 確認 **Hello World！** 出現在文字方塊中。

## <a name="next-steps"></a>下一步
 本逐步解說示範在 Word 文件上使用按鈕和文字方塊的基本概念。 接著可以執行下列一些工作：

- 使用下拉式方塊變更格式。 如需詳細資訊，請參閱 [逐步解說：使用 CheckBox 控制項變更檔案格式](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)。

- 使用選項按鈕以選取圖表樣式。 如需詳細資訊，請參閱 [逐步解說：使用選項按鈕更新檔中的圖表](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)。

## <a name="see-also"></a>另請參閱
- [Office 檔上的 Windows Forms 控制項總覽](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [使用 Word 的逐步解說](../vsto/walkthroughs-using-word.md)
- [Office 開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)
- [如何：將 Windows Forms 控制項新增至 Office 檔](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
