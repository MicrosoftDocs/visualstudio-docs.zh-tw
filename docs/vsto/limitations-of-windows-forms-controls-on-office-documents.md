---
title: "限制的 Windows Form Office 文件上的控制項 |Microsoft 文件"
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
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], ActiveX legacy
- ActiveX controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], limitations
- controls [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], unsupported properties and methods
- Toolbox [Office development in Visual Studio], unsupported controls
- user controls [Office development in Visual Studio], grouping controls
- Windows Forms controls [Office development in Visual Studio], Toolbox
ms.assetid: 95ff473e-4952-4977-bc88-c77289c9fb0b
caps.latest.revision: "56"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6f8842bd80832211f02532ca706416416325663b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Office 文件上的 Windows Form 控制項限制
  有一些 Microsoft Office Word 文件或 Microsoft Office Excel 工作表中，加入 Windows Form 控制項和 Windows Form 控制項加入至 Windows Form 之間的差異。 例如，當您將加入<xref:Microsoft.Office.Tools.Word.Controls.Button>這類控制項加入文件中，屬性<xref:Microsoft.Office.Tools.Word.Controls.Button.Dock%2A>， <xref:Microsoft.Office.Tools.Word.Controls.Button.Anchor%2A>，和<xref:Microsoft.Office.Tools.Word.Controls.Button.TabIndex%2A>未如您預期運作。  
  
 許多這些差異的原因的方式裝載控制項的 Windows Form 上的文件。 當 Windows Form 控制項加入文件，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]嵌入然後裝載文件中的 Windows Form 控制項的 ActiveX 控制項。 在 Windows Form 控制項不會直接在文件中內嵌。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Windows Form 控制項的方法和屬性的限制  
 有許多方法和 Windows Form 控制項無法運作方式相同文件以及它們會在 Windows Form 上，因此，建議不使用這些屬性。 例如，設定屬性，例如`Dock`和`Anchor`只會影響相對於容器 ActiveX 控制項，而不是文件控制項的位置。 不支援的方法和屬性的清單 Word 和 Excel 的 Windows Form 控制項如下：  
  
-   不支援的方法和屬性的 Excel 控制項：  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
-   不支援的方法和屬性的 Word 控制項：  
  
    -   `Hide`  
  
    -   `Show`  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
    -   `Visible`  
  
 您也無法設定`Left`或`Top`與 Word 文件上的文字對齊的 Windows Form 控制項的屬性。 Windows Form 控制項加入與下列情況中的文字對齊：  
  
-   您以程式設計方式將控制項加入 Word 文件，並使用指定的範圍位置的方法。  
  
-   在設計階段將 Windows Form 控制項加入 Word 文件中。 您可以修改設計工具中的控制項來變更。  
  
## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Office 文件上的 Windows Form 控制項中的差異  
 在 Windows Form 上，但確實存在一些差異 Windows Form 控制項通常在 Office 文件上有相同的行為。 下表描述的差異在於 Office 文件上的 Windows Form 控制項。  
  
|功能|差異|  
|-------------------|----------------|  
|控制項定位順序|您無法透過控制項放在 Excel 工作表或 Word 文件索引標籤。|  
|控制項群組|您無法使用<xref:System.Windows.Forms.GroupBox>以包含 Office 文件上的其他控制項的控制項。 當您將多個選項按鈕直接加入文件時，選項按鈕不會互斥。 您可以撰寫程式碼，讓選項按鈕的互斥。不過，慣用的方法是將選項按鈕加入至使用者控制項，然後將使用者控制項加入文件。 如需詳細資訊，請參閱 Word 控制項範例或 Excel 控制項範例： [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)。|  
|控制項類型|文件上使用的 Windows Form 控制項中所提供的類別包裝[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]的 Excel 工作表或 Word 文件提供的控制項專屬的其他功能。 例如，如果您有`Button`控制 Excel 工作表上，請務必將類型指定為<xref:Microsoft.Office.Tools.Excel.Controls.Button>而非<xref:System.Windows.Forms.Button>參考，或將物件轉型時。|  
|控制項位置和大小|大小和控制項的位置會取決於屬於 ActiveX 控制項容器的屬性。 ActiveX 控制項屬性需要不同的值比對等的 Windows Form 控制項的屬性。 當您將`Top`， `Left`， `Height`，或`Width`控制項的屬性，其測量單位是點，而不是像素為單位。|  
|Word 文件上的控制項位置|如果您將控制項加入 流程版面配置時，請記住，控制項會流動內容做為內容變更。 當您將它從拖曳，您無法錨定至段落控制項**工具箱**因為控制項加入 Word 文件，並與文字對齊。 如果您使用另一種方法來加入控制項，例如按兩下控制項，控制項插入根據您已設定為插入圖片的 [文字] 選項。<br /><br /> 您不能設定`Left`或`Top`是內嵌於文字的控制項的屬性。<br /><br /> 您無法將控制項放在頁首或頁尾，或是在子文件。|  
|控制項事件|選取控制項時，它就會引發事件依下列順序：<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> 取消選取控制項時，它會引發事件依下列順序：<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|  
|縮放控制項|當您變更文件的縮放設定為 100%以外的任何項目時，會停用控制項，雖然它們會顯示擴充的文件。 比方說，如果您按一下按鈕，在 130%放大文件時，它會顯示訊息控制項已停用，直到設定縮放為 100%。 當您變更為縮放層級為 100%時，控制項將會正常運作。|  
|控制項屬性值|雖然在 Windows Form 上控制項的屬性會設定為整數值，它們會設定為單一 Word 文件上的控制項。 在 Excel 中，控制項的屬性值會設定成 double。 如果`Height`和`Width`屬性工作表上的控制項超出的工作表或螢幕大小，則會截斷值。|  
|控制項調整大小|如果您調整使用其中一個八個調整大小控點的文件上的控制項，新的控制項維度不會反映在**屬性**直到則在重新選取控制項的視窗。|  
|控制行為|Excel 工作表上的控制項可能會在工作表視窗分割時不正常的行為。 例如，若要存取<xref:Microsoft.Office.Tools.Excel.Controls.TextBox>工作表上只可以在其中一個視窗中。|  
|控制項命名|您無法使用保留的字名稱的控制項。 例如，如果您加入<xref:Microsoft.Office.Tools.Excel.Controls.Button>加入工作表並將名稱變更為**系統**，當您建置專案時，會發生錯誤。|  
|以程式設計方式加入控制項|請勿將控制項加入文件，在執行階段使用控制項的建構函式。 相反地，使用所提供的協助程式方法[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。 例如，使用<xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A>方法，將按鈕加入至工作表。 如果您想要加入的控制項不支援這些 helper 方法，您可以使用 AddControl 方法。 如需詳細資訊，請參閱 [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md)。|  
|複製控制項|如果您複製的 Windows Form 控制項，並將它貼到文件中，在執行階段，會將空的 ActiveX 控制項容器貼入文件。 不會顯示在 Windows Form 控制項，這是在新的位置，以及程式碼後置原始控制項不會複製到容器 ActiveX 控制項。|  
  
## <a name="limitations-in-document-level-projects"></a>在文件層級專案中的限制  
 使用文件上的 Windows Form 控制項的某些限制是文件層級專案中唯一的。  
  
### <a name="control-support-at-design-time"></a>在設計階段控制項支援  
 特定的 Windows Form 控制項，就會自**工具箱**當 Excel 工作表或 Word 文件是在 Visual Studio 設計工具中開啟。 這是因為技術限制，或因為已經使用 Word 或 Excel 中的功能。 Excel 和 Word 專案支援的 Windows Form 控制項和其他元件中出現的所有**工具箱**當文件具有焦點，而且您也可以將協力廠商控制項加入工作表或文件。  
  
> [!NOTE]  
>  所有控制項都移除了**工具箱**文件受到保護時。 如需文件保護的詳細資訊，請參閱[文件層級方案中的文件保護](../vsto/document-protection-in-document-level-solutions.md)。  
  
> [!NOTE]  
>  第三方勂厞饡瑢<xref:System.Runtime.InteropServices.ComVisibleAttribute>屬性設為**true**才能使用 Office 方案中。  
  
 下列控制項和元件中沒有**工具箱**:  
  
-   <xref:System.Windows.Forms.BindingNavigator>  
  
-   <xref:System.Windows.Forms.ContextMenuStrip>  
  
-   <xref:System.Windows.Forms.DataGrid>  
  
-   <xref:System.DirectoryServices.DirectoryEntry>  
  
-   <xref:System.DirectoryServices.DirectorySearcher>  
  
-   <xref:System.Windows.Forms.ErrorProvider>  
  
-   <xref:System.Diagnostics.EventLog>  
  
-   <xref:System.IO.FileSystemWatcher>  
  
-   <xref:System.Windows.Forms.FlowLayoutPanel>  
  
-   <xref:System.Windows.Forms.GroupBox>  
  
-   <xref:System.Windows.Forms.MainMenu>  
  
-   <xref:System.Windows.Forms.MenuStrip>  
  
-   <xref:System.Messaging.MessageQueue>  
  
-   <xref:System.Windows.Forms.NotifyIcon>  
  
-   <xref:System.Windows.Forms.PageSetupDialog>  
  
-   <xref:System.Windows.Forms.Panel>  
  
-   <xref:System.Diagnostics.PerformanceCounter>  
  
-   <xref:System.Windows.Forms.PrintDialog>  
  
-   <xref:System.Drawing.Printing.PrintDocument>  
  
-   <xref:System.Windows.Forms.PrintPreviewControl>  
  
-   <xref:System.Diagnostics.Process>  
  
-   <xref:System.Windows.Forms.RichTextBox>  
  
-   <xref:System.IO.Ports.SerialPort>  
  
-   <xref:System.ServiceProcess.ServiceController>  
  
-   <xref:System.Windows.Forms.SplitContainer>  
  
-   <xref:System.Windows.Forms.Splitter>  
  
-   <xref:System.Windows.Forms.StatusBar>  
  
-   <xref:System.Windows.Forms.StatusStrip>  
  
-   <xref:System.Windows.Forms.TabControl>  
  
-   <xref:System.Windows.Forms.TableLayoutPanel>  
  
-   <xref:System.Timers.Timer>  
  
-   <xref:System.Windows.Forms.Timer>  
  
-   <xref:System.Windows.Forms.ToolBar>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
-   <xref:System.Windows.Forms.ToolStripContainer>  
  
-   <xref:System.Windows.Forms.ToolStripDropDown>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownMenu>  
  
-   <xref:System.Windows.Forms.ToolStripPanel>  
  
### <a name="support-for-legacy-activex-controls"></a>支援的舊版 ActiveX 控制項  
 如果您建立使用現有的 Word 文件或包含 ActiveX 控制項的 Excel 活頁簿的文件層級 Office 專案時，ActiveX 控制項的功能不會遺失。不過，沒有您從 Visual Studio 中的文件中加入新的 ActiveX 控制項的支援。 例如，如果您的 Word 文件有一個按鈕，從**控制項**工具箱 中執行 Visual Basic for Applications (VBA) 巨集，它會繼續已在 Office 專案中使用文件之後，執行巨集。 不過，建議您移除 ActiveX 控制項和 VBA 巨集和取代 Windows Form 控制項和 managed 程式碼。  
  
## <a name="see-also"></a>另請參閱  
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [Windows Form 控制項，在 Office 文件概觀](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [在執行階段將控制項加入 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [如何：將 Windows Forms 控制項新增至 Office 文件](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)  
  
  