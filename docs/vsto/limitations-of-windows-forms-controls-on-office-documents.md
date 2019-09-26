---
title: Office 檔上的 Windows Forms 控制項限制
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], ActiveX legacy
- ActiveX controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], limitations
- controls [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], unsupported properties and methods
- Toolbox [Office development in Visual Studio], unsupported controls
- user controls [Office development in Visual Studio], grouping controls
- Windows Forms controls [Office development in Visual Studio], Toolbox
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 81a7da585f49b2a2d1f7df4df11d0c78b7a35d69
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71251921"
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Office 檔上的 Windows Forms 控制項限制

Windows Forms 控制項（加入至 Microsoft Office Word 檔或 Microsoft Office Excel 工作表）與 Windows Forms 控制項（加入 Windows Forms）之間有一些差異。 例如<xref:Microsoft.Office.Tools.Word.Controls.Button> ，當您將控制項加入至檔時， <xref:System.Windows.Forms.Control.Dock>、 <xref:System.Windows.Forms.Control.Anchor>和<xref:System.Windows.Forms.Control.TabIndex>等屬性的行為不會如您預期般運作。

其中有許多差異是因為 Windows Forms 控制項裝載在檔上的方式所造成。 當 Windows Forms 控制項加入至檔時， [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]會內嵌 ActiveX 控制項，然後在檔中主控 Windows Forms 控制項。 Windows Forms 控制項不會直接內嵌在檔中。

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Windows Forms 控制項的方法和屬性限制

Windows Forms 控制項有許多方法和屬性，在檔上的使用方式與在 Windows Form 上的效果相同，因此建議不要使用它們。 例如，設定屬性（ <xref:System.Windows.Forms.Control.Dock>例如和<xref:System.Windows.Forms.Control.Anchor> ）只會影響控制項相對於容器 ActiveX 控制項的位置，而非檔。 以下是 Word 和 Excel 的 Windows Forms 控制項不支援的方法和屬性清單：

- 不支援的 Excel 控制項屬性：

  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>

- Word 控制項不支援的方法和屬性：

  - <xref:System.Windows.Forms.Control.Hide%2A>
  - <xref:System.Windows.Forms.Control.Show%2A>
  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>
  - <xref:System.Windows.Forms.Control.Visible>

您也無法在 Word <xref:System.Windows.Forms.Control.Left>檔<xref:System.Windows.Forms.Control.Top>上，設定以文字為行之 Windows Forms 控制項的或屬性。 在下列情況下，會將 Windows Forms 控制項加入至包含文字的行：

- 您以程式設計方式將控制項新增至 Word 檔，並使用方法來指定位置的範圍。

- 在設計階段，您會將 Windows Forms 控制項新增至 Word 檔。 您可以藉由修改設計工具中的控制項來變更此項。

## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Office 檔上 Windows Forms 控制項的差異

Windows Forms 控制項在 Office 檔上通常會有相同的行為，就像是在 Windows Form 上一樣，但有一些差異存在。 下表描述 Windows Forms 控制項在 Office 檔上存在的差異。

|功能|差異|
|-------------------|----------------|
|控制索引標籤順序|您無法透過索引標籤，在 Excel 工作表或 Word 檔上放置控制項。|
|控制項群組|您不能使用<xref:System.Windows.Forms.GroupBox>控制項來包含 Office 檔上的其他控制項。 當您將多個選項按鈕直接加入檔時，選項按鈕不會互斥。 您可以撰寫程式碼，讓選項按鈕與互斥;不過，慣用的方法是將選項按鈕加入至使用者控制項，然後將使用者控制項加入檔中。 如需詳細資訊，請參閱[Office 程式開發範例和](../vsto/office-development-samples-and-walkthroughs.md)逐步解說中的 Word 控制項範例或 Excel 控制項範例。|
|控制項類型|在檔上使用的 Windows Forms 控制項會包裝在所[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]提供的類別中，讓控制項能夠控制 Excel 工作表或 Word 檔的其他功能。 例如，如果您有 **按鈕** 控制項上的 Excel 工作表，請務必將類型指定為<xref:Microsoft.Office.Tools.Excel.Controls.Button>而非<xref:System.Windows.Forms.Button>參考，或將物件轉型時。|
|控制位置和大小|控制項的大小和位置是由屬於容器 ActiveX 控制項一部分的屬性所決定。 ActiveX 控制項屬性接受的值不同于 Windows Forms 控制項的對等屬性。 當您設定控制項`Top`的`Left`、 `Height`、或`Width`屬性時，會以點來測量，而不是以圖元為單位。|
|在 Word 檔上控制位置|如果您將控制項新增至以流程為基礎的配置，請記住，當內容變更時，控制項會與內容一起流動。 當您從 [**工具箱**] 拖曳控制項時，無法將它錨定到段落，因為該控制項會以文字行加入 Word 檔中。 如果您使用另一個方法來加入控制項（例如按兩下控制項），就會根據您為 [插入圖片] 所設定的 [文字] 選項來插入控制項。<br /><br /> 您不能設定`Left`以`Top`文字內嵌之控制項的或屬性。<br /><br /> 您不能將控制項放在頁首或頁尾，或子檔內。|
|控制項事件|選取控制項時，它會依下列順序引發事件：<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> 取消選取控制項時，它會依下列順序引發事件：<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|
|控制調整|當您將檔的 [縮放] 設定變更為 [100%] 以外的任何值時，就會停用控制項，雖然它們似乎會隨著檔調整。 例如，如果您在檔處於 130% zoom 時按一下按鈕，它會顯示一則訊息，表示控制項已停用，直到 zoom 設定為 100% 為止。 當您將縮放比例變更為 100% 時，控制項將會正常運作。|
|控制項屬性值|雖然 Windows Form 上控制項的屬性會設定為整數值，但它們會設定為 Word 檔上控制項的單一。 在 Excel 中，控制項的屬性值會設定為 double。 如果工作`Height`表`Width`上控制項的和屬性超過工作表或螢幕的大小，則會截斷此值。|
|控制項調整大小|如果您使用八個調整大小控點的其中一個來調整檔的控制項大小，新的控制項維度在問題控制項之前，不會反映在 [**屬性**] 視窗中。|
|控制行為|當工作表視窗被分割時，Excel 工作表上的控制項可能會以無法預期的方式運作。 例如，對工作表上<xref:Microsoft.Office.Tools.Excel.Controls.TextBox>的的存取權只能在其中一個視窗中使用。|
|控制項命名|您不能使用保留字來命名控制項。 例如，如果您將加入<xref:Microsoft.Office.Tools.Excel.Controls.Button>至工作表，並將名稱變更為 [**系統**]，當您建立專案時就會發生錯誤。|
|以程式設計方式加入控制項|請勿使用控制項的函式，在執行時間將控制項加入至您的檔。 相反地，請使用所提供[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]的 helper 方法。 例如，使用<xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A>方法將按鈕新增至工作表。 如果您想要新增這些 helper 方法不支援的控制項，您可以使用`AddControl`方法。 如需詳細資訊，請參閱[在執行時間將控制項加入 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)。|
|複製控制項|如果您在執行時間複製 Windows Forms 控制項並將它貼到檔中，則會將空的容器 ActiveX 控制項貼入檔中。 Windows Forms 控制項不會出現在新的位置中，而且原始控制項背後的程式碼不會複製到容器 ActiveX 控制項。|

## <a name="limitations-in-document-level-projects"></a>檔層級專案的限制

在檔上使用 Windows Forms 控制項的一些限制，對檔層級專案而言是唯一的。

### <a name="control-support-at-design-time"></a>設計階段的控制項支援

當 Excel 工作表或 Word 檔在 Visual Studio 設計工具中開啟時，就會從 [**工具箱**] 中移除某些 Windows Forms 控制項。 這是因為技術上的限制，或是 Word 或 Excel 中的功能已可供使用。 Excel 和 Word 專案支援當檔具有焦點時，出現在 [**工具箱**] 中的所有 Windows Forms 控制項和其他元件，而且您也可以將協力廠商控制項加入工作表或檔中。

> [!NOTE]
> 當檔受到保護時，所有控制項都會從 [**工具箱**] 中移除。 如需檔案保護的詳細資訊，請參閱檔[層級方案中的檔案保護](../vsto/document-protection-in-document-level-solutions.md)。

> [!NOTE]
> 協力廠商控制項必須<xref:System.Runtime.InteropServices.ComVisibleAttribute>將屬性設定為**true** ，才能在 Office 方案中使用。

下列控制項和元件在 [**工具箱**] 中無法使用：

- <xref:System.Windows.Forms.BindingNavigator>

- <xref:System.Windows.Forms.ContextMenuStrip>

- <xref:System.Windows.Forms.DataGrid>

- <xref:System.DirectoryServices.DirectoryEntry>

- <xref:System.DirectoryServices.DirectorySearcher>

- <xref:System.Windows.Forms.ErrorProvider>

- <xref:System.Diagnostics.EventLog>

- <xref:System.IO.FileSystemWatcher>

- <xref:System.Windows.Forms.FlowLayoutPanel>

- <xref:System.Windows.Forms.GroupBox>

- <xref:System.Windows.Forms.MainMenu>

- <xref:System.Windows.Forms.MenuStrip>

- <xref:System.Messaging.MessageQueue>

- <xref:System.Windows.Forms.NotifyIcon>

- <xref:System.Windows.Forms.PageSetupDialog>

- <xref:System.Windows.Forms.Panel>

- <xref:System.Diagnostics.PerformanceCounter>

- <xref:System.Windows.Forms.PrintDialog>

- <xref:System.Drawing.Printing.PrintDocument>

- <xref:System.Windows.Forms.PrintPreviewControl>

- <xref:System.Diagnostics.Process>

- <xref:System.Windows.Forms.RichTextBox>

- <xref:System.IO.Ports.SerialPort>

- <xref:System.ServiceProcess.ServiceController>

- <xref:System.Windows.Forms.SplitContainer>

- <xref:System.Windows.Forms.Splitter>

- <xref:System.Windows.Forms.StatusBar>

- <xref:System.Windows.Forms.StatusStrip>

- <xref:System.Windows.Forms.TabControl>

- <xref:System.Windows.Forms.TableLayoutPanel>

- <xref:System.Timers.Timer>

- <xref:System.Windows.Forms.Timer>

- <xref:System.Windows.Forms.ToolBar>

- <xref:System.Windows.Forms.ToolStrip>

- <xref:System.Windows.Forms.ToolStripContainer>

- <xref:System.Windows.Forms.ToolStripDropDown>

- <xref:System.Windows.Forms.ToolStripDropDownMenu>

- <xref:System.Windows.Forms.ToolStripPanel>

### <a name="support-for-legacy-activex-controls"></a>舊版 ActiveX 控制項的支援

如果您建立的檔層級 Office 專案使用包含 ActiveX 控制項的現有 Word 檔或 Excel 活頁簿，則 ActiveX 控制項的功能不會遺失;不過，不支援在 Visual Studio 中將新的 ActiveX 控制項新增至您的檔。 例如，如果 Word 檔具有可執行 Visual Basic for Applications （VBA）宏的 [**控制**工具箱] 按鈕，則在 Office 專案中使用檔之後，它會繼續執行宏。 不過，建議您移除 ActiveX 控制項和 VBA 宏，並將其取代為 Windows Forms 控制項和 managed 程式碼。

## <a name="see-also"></a>另請參閱

- [Office 檔上的控制項](../vsto/controls-on-office-documents.md)
- [Office 檔上的 Windows Forms 控制項總覽](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [在執行時間將控制項加入 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [如何：將 Windows Forms 控制項加入 Office 檔](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
