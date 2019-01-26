---
title: Office 文件上的 Windows Form 控制項的限制
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
ms.openlocfilehash: 610ee5e18054b6da35a3098b851d1585c70b6bc3
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863538"
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Office 文件上的 Windows Form 控制項的限制

有一些會新增至 Microsoft Office Word 文件或 Microsoft Office Excel 工作表的 Windows Form 控制項和 Windows Form 控制項加入至 Windows Form 之間的差異。 比方說，當您新增<xref:Microsoft.Office.Tools.Word.Controls.Button>這類控制項加入文件，而屬性<xref:System.Windows.Forms.Control.Dock>， <xref:System.Windows.Forms.Control.Anchor>，和<xref:System.Windows.Forms.Control.TabIndex>您預期不會運作。

許多這些差異會造成附帶一提該控制項所裝載的 Windows Form 上的文件。 當 Windows Form 控制項加入文件、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]內嵌 ActiveX 控制項，然後裝載在 Windows Form 控制項在文件。 在 Windows Form 控制項不會直接在文件中內嵌。

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Windows Form 控制項的方法和屬性的限制

有許多方法和屬性無法運作的相同方式在文件上以及它們會在 Windows Form 上，因此，建議您使用它們不會用的 Windows Form 控制項。 比方說，這類設定屬性<xref:System.Windows.Forms.Control.Dock>和<xref:System.Windows.Forms.Control.Anchor>只會影響相對於容器 ActiveX 控制項，而不是文件控制項的位置。 不支援的方法與 Word 和 Excel 的 Windows Form 控制項的屬性清單如下：

- 不支援的 Excel 控制項的屬性：

    - <xref:System.Windows.Forms.Control.Anchor>
    - <xref:System.Windows.Forms.Control.Dock>
    - <xref:System.Windows.Forms.Control.Location>
    - <xref:System.Windows.Forms.Control.TabIndex>
    - <xref:System.Windows.Forms.Control.TabStop>
    - <xref:System.Windows.Forms.Control.TopLevelControl>

- 不支援的方法和屬性的 Word 控制項：

    - <xref:System.Windows.Forms.Control.Hide%2A>
    - <xref:System.Windows.Forms.Control.Show%2A>
    - <xref:System.Windows.Forms.Control.Anchor>
    - <xref:System.Windows.Forms.Control.Dock>
    - <xref:System.Windows.Forms.Control.Location>
    - <xref:System.Windows.Forms.Control.TabIndex>
    - <xref:System.Windows.Forms.Control.TabStop>
    - <xref:System.Windows.Forms.Control.TopLevelControl>
    - <xref:System.Windows.Forms.Control.Visible>

您也無法設定<xref:System.Windows.Forms.Control.Left>或<xref:System.Windows.Forms.Control.Top>與 Word 文件上的文字對齊的 Windows Form 控制項的屬性。 Windows Form 控制項加入與下列案例中的文字對齊：

- 您以程式設計方式將控制項加入 Word 文件，並使用指定的位置範圍的方法。

- 在設計階段將 Windows Forms 控制項加入 Word 文件中。 您可以修改設計工具中的控制項來變更。

## <a name="differences-in-windows-forms-controls-on-office-documents"></a>在 Office 文件上的 Windows Form 控制項中的差異

Windows Form 控制項通常會對相同的行為 Office 文件上 Windows 表單中，但確實存在一些差異。 下表描述 Office 文件上的 Windows Form 控制項所存在的差異。

|功能|差異|
|-------------------|----------------|
|控制項定位順序|您無法透過在 Excel 工作表或 Word 文件上放置控制項的索引標籤。|
|控制項群組|您無法使用<xref:System.Windows.Forms.GroupBox>包含 Office 文件上的其他控制項的控制項。 當您將多個選項按鈕直接加入文件時，不是互斥的選項按鈕。 您可以撰寫程式碼，讓選項按鈕是互斥的;不過，慣用的方法是新增至使用者控制項的選項按鈕，然後將使用者控制項加入文件。 如需詳細資訊，請參閱 Word 控制項範例或 Excel 控制項範例： [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)。|
|控制項類型|文件上使用的 Windows Form 控制項中所提供的類別包裝[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]的 Excel 工作表或 Word 文件提供的控制項特定的其他功能。 例如，如果您有** 按鈕**控制項上的 Excel 工作表，請務必將類型指定為<xref:Microsoft.Office.Tools.Excel.Controls.Button>而非<xref:System.Windows.Forms.Button>參考，或將物件轉型時。|
|控制項位置和大小|大小和控制項的位置取決於屬性屬於的 ActiveX 控制項的容器。 ActiveX 控制項的屬性會採用不同的值，比 Windows Forms 控制項的對等的屬性。 當您設定`Top`， `Left`， `Height`，或`Width`控制項的屬性，其測量單位是點，而不是像素為單位。|
|Word 文件上的控制項位置|如果您將控制項加入流程為基礎的版面配置時，請記住，控制項會使用內容流動內容的變更。 您無法控制項錨定至段落時您將它從拖曳**工具箱**因為控制項加入 Word 文件，與文字對齊。 如果您使用另一種方法來新增控制項，例如按兩下控制項，會將控制項插入根據您已設定為插入圖片的 [Word] 選項。<br /><br /> 您無法設定`Left`或`Top`是內嵌於文字控制項的屬性。<br /><br /> 您無法將控制項放在頁首或頁尾中，或在子文件。|
|控制項事件|選取控制項時，它會引發事件，以下列順序：<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> 取消選取控制項，它會引發事件，以下列順序：<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|
|控制項縮放比例|當您以 100%以外的任何變更的文件的縮放設定時，已停用控制項，雖然看起來就像會隨著文件。 比方說，如果您按一下按鈕，在 130%放大您的文件時，它會顯示一則訊息控制項已停用，直到設定縮放為 100%。 當您變更為縮放層級為 100%時，控制項將會正常運作。|
|控制項屬性的值|雖然在 Windows Form 上控制項的屬性會設定為整數值，它們會設定為在單一 Word 文件上的控制項。 在 Excel 中，控制項的屬性值會設定為雙精度浮點數。 如果`Height`和`Width`屬性工作表上的控制項超出工作表或螢幕大小，則會截斷值。|
|控制項調整大小|如果您調整大小的八個調整大小控點使用的文件上的控制項，新的控制項維度不會反映在**屬性**之前在控制項的視窗。|
|控制行為|在 Excel 工作表上的控制項可能會在工作表視窗分割時不正常的行為。 例如，若要存取<xref:Microsoft.Office.Tools.Excel.Controls.TextBox>工作表上只可在其中一個視窗中。|
|控制命名|您無法使用保留的字來命名控制項。 比方說，如果您加入<xref:Microsoft.Office.Tools.Excel.Controls.Button>加入工作表並將名稱變更為**系統**，當您建置專案時，會發生錯誤。|
|以程式設計方式加入控制項|請勿將控制項新增至您的文件，在執行階段使用控制項的建構函式。 相反地，使用所提供的協助程式方法[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。 例如，使用<xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A>方法，將按鈕加入至工作表。 如果您想要新增的控制項，不支援這些 helper 方法，您可以使用`AddControl`方法。 如需詳細資訊，請參閱 <<c0> [ 將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)。|
|複製控制項|如果您複製的 Windows Form 控制項，並將它貼到文件在執行階段，會將空的 ActiveX 控制項容器貼入文件。 不會顯示在 Windows Form 控制項，這是在新的位置，以及程式碼後置原始控制項不會複製到容器的 ActiveX 控制項。|

## <a name="limitations-in-document-level-projects"></a>在文件層級專案中的限制

使用文件上的 Windows Form 控制項的某些限制是唯一的文件層級專案。

### <a name="control-support-at-design-time"></a>在設計階段控制項支援

從移除特定的 Windows Forms 控制項**工具箱**Excel 工作表或 Word 文件時在 Visual Studio 設計工具中開啟。 這是因為技術限制，或因為已使用 Word 或 Excel 中的功能。 Excel 和 Word 專案支援的 Windows Forms 控制項和其他元件中出現的所有**工具箱**當文件有焦點，而且您也可以將協力廠商控制項加入工作表或文件。

> [!NOTE]
> 所有控制項都移除了**工具箱**受保護文件時。 如需文件保護資訊，請參閱[文件的文件層級方案中的保護](../vsto/document-protection-in-document-level-solutions.md)。

> [!NOTE]
> 第三方勂厞饡瑢<xref:System.Runtime.InteropServices.ComVisibleAttribute>屬性設為 **，則為 true**才能使用 Office 方案中。

下列控制項和元件不適用於**工具箱**:

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

### <a name="support-for-legacy-activex-controls"></a>支援的舊版 ActiveX 控制項

如果您建立使用現有的 Word 文件或 Excel 活頁簿包含 ActiveX 控制項的文件層級 Office 專案時，ActiveX 控制項的功能不會遺失。不過，沒有您從 Visual Studio 內的文件中加入新的 ActiveX 控制項的支援。 例如，如果您的 Word 文件有一個按鈕，從**控制**執行 Visual Basic for Applications (VBA) 巨集的工具箱中，它將會繼續執行巨集之後已使用 Office 專案中的文件。 不過，建議您移除 ActiveX 控制項與 VBA 巨集和它們取代成 Windows Form 控制項和 managed 程式碼。

## <a name="see-also"></a>另請參閱

- [Office 文件上的控制項](../vsto/controls-on-office-documents.md)
- [在 Office 文件概觀上的 Windows Form 控制項](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [如何：將 Windows Form 控制項加入 Office 文件](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)