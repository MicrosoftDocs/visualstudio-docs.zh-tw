---
title: Office 檔上 Windows Forms 控制項的限制
description: 瞭解 Microsoft Office 檔上 Windows Forms 控制方法和屬性的限制。
ms.custom: SEO-VS-2020
titleSuffix: ''
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
ms.openlocfilehash: 63459f4daf1f9fe717946491a997ba47510fbab8
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524446"
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Office 檔上 Windows Forms 控制項的限制

加入至 Microsoft Office Word 檔或 Microsoft Office Excel 工作表的 Windows Forms 控制項，以及新增至 Windows Forms 的 Windows Forms 控制項之間有一些差異。 例如，當您將控制項加入 <xref:Microsoft.Office.Tools.Word.Controls.Button> 至檔時，如、和等屬性的 <xref:System.Windows.Forms.Control.Dock> <xref:System.Windows.Forms.Control.Anchor> <xref:System.Windows.Forms.Control.TabIndex> 行為並不會如您預期般運作。

其中許多差異是因為在檔上裝載 Windows Forms 控制項的方式所造成。 當 Windows Forms 控制項新增至檔時，會 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 內嵌 ActiveX 控制項，然後在檔中裝載 Windows Forms 控制項。 Windows Forms 控制項不會直接內嵌在檔中。

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Windows Forms 控制項的方法和屬性限制

Windows Forms 控制項有許多方法和屬性在檔上的運作方式，與在 Windows Form 上的運作方式相同，因此建議您不要使用它們。 例如，設定屬性（例如 <xref:System.Windows.Forms.Control.Dock> 和） <xref:System.Windows.Forms.Control.Anchor> 只會影響控制項相對於容器 ActiveX 控制項的位置，而不會影響檔的位置。 以下是 Word 和 Excel 的 Windows Forms 控制項不支援的方法和屬性清單：

- 不支援的 Excel 控制項屬性：

  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>

- 不支援的 Word 控制項方法和屬性：

  - <xref:System.Windows.Forms.Control.Hide%2A>
  - <xref:System.Windows.Forms.Control.Show%2A>
  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>
  - <xref:System.Windows.Forms.Control.Visible>

您也無法設定 <xref:System.Windows.Forms.Control.Left> <xref:System.Windows.Forms.Control.Top> Windows Forms 控制項的或屬性，其與 Word 檔中的文字有關。 在下列情況下，會將 Windows Forms 控制項新增至文字：

- 您以程式設計方式將控制項新增至 Word 檔，並使用指定位置範圍的方法。

- 您可以在設計階段將 Windows Forms 控制項加入 Word 檔中。 您可以藉由在設計工具中修改控制項來變更。

## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Office 檔的 Windows Forms 控制項差異

Windows Forms 控制項在 Office 檔上的行為通常與 Windows Form 上的行為相同，但是有一些差異存在。 下表描述 Office 檔上 Windows Forms 控制項的存在差異。

|功能|差數|
|-------------------|----------------|
|控制項定位順序|您無法透過定位於 Excel 工作表或 Word 檔上的控制項來定位。|
|控制項群組|您無法使用 <xref:System.Windows.Forms.GroupBox> 控制項來包含 Office 檔上的其他控制項。 當您將多個選項按鈕直接新增至檔時，選項按鈕不會互斥。 您可以撰寫程式碼來使選項按鈕彼此互斥;不過，慣用的方法是將選項按鈕加入至使用者控制項，然後將使用者控制項加入檔。 如需詳細資訊，請參閱 [Office 程式開發範例和](../vsto/office-development-samples-and-walkthroughs.md)逐步解說中的 Word 控制項範例或 Excel 控制項範例。|
|控制項類型|檔上所使用的 Windows Forms 控制項會包裝在所提供的類別中 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ，提供給控制項其他 Excel 工作表或 Word 檔專屬的功能。 例如，如果您在 Excel 工作表上有一個 **按鈕** 控制項，請務必將類型指定為， <xref:Microsoft.Office.Tools.Excel.Controls.Button> 而不是 <xref:System.Windows.Forms.Button> 在參考或轉換物件時指定。|
|控制項位置和大小|控制項的大小和位置取決於屬於容器 ActiveX 控制項一部分的屬性。 ActiveX 控制項屬性所採用的值與 Windows Forms 控制項的相等屬性不同。 當您設定 `Top` 控制項的、 `Left` 、或屬性時， `Height` `Width` 會以點為單位來測量，而不是以圖元為單位。|
|在 Word 檔上控制位置|如果您將控制項加入以流程為基礎的版面配置，請記住，當內容變更時，控制項會與內容一起流動。 當您從 [ **工具箱** ] 拖曳控制項時，無法將該控制項錨定至段落，因為該控制項會以文字加入 Word 檔中。 如果您使用另一個方法來加入控制項（例如按兩下控制項），則會根據您為插入圖片所設定的單字選項來插入控制項。<br /><br /> 您無法設定 `Left` `Top` 內嵌于文字之控制項的或屬性。<br /><br /> 您無法將控制項放在頁首或頁尾中，或放在子檔內。|
|控制事件|選取控制項時，它會依下列順序引發事件：<br /><br /> 單.  `Enter`<br />二級.  `GotFocus`<br /><br /> 當取消選取控制項時，它會依下列順序引發事件：<br /><br /> 單.  `Leave`<br />二級.  `Validating`<br />3.  `Validated`<br />億.  `LostFocus`|
|控制項調整|當您將檔的縮放設定變更為100% 以外的任何值時，就會停用控制項，雖然它們看起來與檔調整一樣。 例如，如果您在檔處於 130% zoom 時按一下按鈕，就會顯示一則訊息，指出控制項已停用，直到 zoom 設定為100% 為止。 當您將縮放比例變更為100% 時，控制項就會正常運作。|
|控制項屬性值|雖然 Windows Form 上的控制項屬性會設定為整數值，但它們會設定為 Word 檔上控制項的單一。 在 Excel 中，控制項的屬性值會設定為雙精度浮點數。 如果 `Height` `Width` 工作表上控制項的和屬性超過工作表或螢幕的大小，則會截斷此值。|
|控制項調整大小|如果您使用八個調整大小控點的其中一個來調整檔的控制項大小，則在問題控制項之前，新的控制項維度不會反映在 [ **屬性** ] 視窗中。|
|控制行為|當工作表視窗被分割時，Excel 工作表上的控制項可能會以非預期的行為。 例如，工作表的存取權 <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> 只能在其中一個視窗中使用。|
|控制項命名|您不能使用保留字來命名控制項。 例如，如果您將加入 <xref:Microsoft.Office.Tools.Excel.Controls.Button> 至工作表，並將名稱變更為 [ **系統**]，當您建立專案時，就會發生錯誤。|
|以程式設計方式加入控制項|請勿使用控制項的函式在執行時間將控制項加入至您的檔。 相反地，請使用所提供的 helper 方法 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 。 例如，使用 <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> 方法將按鈕加入至工作表。 如果您想要加入這些 helper 方法不支援的控制項，則可以使用 `AddControl` 方法。 如需詳細資訊，請參閱 [在執行時間將控制項加入 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)。|
|複製控制項|如果您複製 Windows Forms 控制項，並在執行時間將它貼到檔中，則會在檔中貼上空白的容器 ActiveX 控制項。 Windows Forms 控制項不會出現在新位置，而且原始控制項的程式碼後置不會複製到容器 ActiveX 控制項。|

## <a name="limitations-in-document-level-projects"></a>檔層級專案的限制

在檔上使用 Windows Forms 控制項的一些限制，對檔層級專案而言是唯一的。

### <a name="control-support-at-design-time"></a>設計階段的控制項支援

當 Excel 工作表或 Word 檔在 Visual Studio 設計工具中開啟時，會從 [ **工具箱** ] 中移除某些 Windows Forms 控制項。 這是因為技術上的限制，或是 Word 或 Excel 中的功能已可供使用。 Excel 和 Word 專案支援當檔具有焦點時，出現在 [ **工具箱** ] 中的所有 Windows Forms 控制項和其他元件，而且您也可以將協力廠商控制項加入工作表或檔中。

> [!NOTE]
> 當檔受到保護時，就會從 [ **工具箱** ] 中移除所有控制項。 如需檔案保護的詳細資訊，請參閱檔 [層級方案中的檔案保護](../vsto/document-protection-in-document-level-solutions.md)。

> [!NOTE]
> 協力廠商控制項必須將 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 屬性設定為 **true** ，才能在 Office 方案中使用。

**工具箱** 中無法使用下列控制項和元件：

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

如果您建立的檔層級 Office 專案使用包含 ActiveX 控制項的現有 Word 檔或 Excel 活頁簿，ActiveX 控制項的功能將不會遺失;但是，不支援將新的 ActiveX 控制項從 Visual Studio 內加入至您的檔。 比方說，如果您的 Word 檔有一個 **控制項** 工具箱中的按鈕，可執行 VISUAL BASIC FOR APPLICATIONS (VBA) 宏，則在 Office 專案中使用檔之後，它會繼續執行宏。 不過，建議您移除 ActiveX 控制項和 VBA 宏，並將它們取代為 Windows Forms 控制項和 managed 程式碼。

## <a name="see-also"></a>另請參閱

- [Office 檔上的控制項](../vsto/controls-on-office-documents.md)
- [Office 檔上的 Windows Forms 控制項總覽](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [在執行時間將控制項新增至 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [如何：將 Windows Forms 控制項新增至 Office 檔](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
