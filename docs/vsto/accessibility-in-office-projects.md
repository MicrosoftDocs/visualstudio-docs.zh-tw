---
title: Office 專案中的協助工具 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, accessibility
- shortcut keys [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], shortcut keys
- accessibility [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8416e3fb5d5f46709870ffc3c7247c564bc845ff
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="accessibility-in-office-projects"></a>Office 專案中的協助工具
  Microsoft Visual Studio 和 Microsoft Office 包含許多協助工具功能可讓您建置自訂的解決方案符合標準的協助工具需求。 Microsoft 會發行在網站上的協助工具的指導方針。 如需詳細資訊，請參閱[協助工具網站](http://go.microsoft.com/fwlink/?LinkID=37113)。  

 在大部分情況下，Visual Studio 中的 Office 專案會符合您可以設定讓您的解決方案都能存取的協助工具標準或公開屬性。 不過，有一些功能，以存取上受到限制。  

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  

## <a name="accessibility-at-design-time"></a>在設計階段的協助工具  

### <a name="using-shortcut-keys-in-document-level-projects"></a>在文件層級專案中使用的快速鍵  
 開啟 Visual Studio 中的 Microsoft Office Word 文件或 Microsoft Office Excel 活頁簿時，一次只有一個應用程式接收快顯命令。 根據預設，Visual Studio 會收到所有捷徑命令，但您可以進行 Word 或 Excel 文件選取具有焦點時，接收這些**動態鍵盤配置**上**鍵盤設定**頁面**選項** 對話方塊。 如需詳細資訊，請參閱[Microsoft Office Word 鍵盤，Microsoft Office 鍵盤設定、 [選項] 對話方塊](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)和[Microsoft Office Excel 鍵盤，Microsoft Office 鍵盤設定、 選項對話方塊](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).  

### <a name="displaying-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>在文件層級專案中功能區顯示快速鍵  
 Visual Studio 中開啟 Word 文件或 Excel 活頁簿時，您無法按下 Alt 鍵，若要檢視的索引標籤及功能區上的控制項的快速鍵。 若要檢視的鍵盤快速鍵，文件或活頁簿設計工具中開啟時，執行下列步驟。  

##### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>若要檢視設計工具中的功能區索引標籤和控制項的快速鍵  

1.  在 Visual Studio 中，在**工具**功能表上，按一下 **選項**。  

2.  展開**Office 工具**節點，然後選取**Microsoft Office Excel 鍵盤**或**Microsoft Office Word 鍵盤**視情況。  

3.  選取**動態鍵盤配置**。  

     此時會出現訊息指出您必須重新啟動 Visual Studio，變更才會生效。  

4.  按一下 [確定 **Deploying Office Solutions**]。  

5.  重新啟動 Visual Studio，並重新開啟您的專案。  

6.  開啟您專案的文件或活頁簿設計工具。  

7.  按 F6 功能區顯示的快速鍵。  

## <a name="accessibility-at-run-time"></a>在執行階段的協助工具  

### <a name="windows-forms-controls-on-office-documents"></a>Windows Form Office 文件上的控制項  
 Windows Form 控制項中公開協助工具屬性，以提供給協助工具輔助，例如螢幕助讀程式控制項的相關資訊。 您可以利用這些協助工具屬性的文件層級自訂中的 Office 文件上的控制項時。 如需詳細資訊，請參閱[提供 Windows Form 上控制項的協助工具資訊](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form)。  

 不過，在執行階段時的 Excel 活頁簿或 Word 文件裝載 Windows Form 控制項有一些協助工具的限制：  

-   您無法以另一個索引標籤從一個控制項。  

-   當您將文件的縮放設定變更為 100%以外的任何項目時，會停用文件上的控制項。  

 如需限制的文件上的 Windows Form 控制項的資訊，請參閱[限制的 Windows Form 控制項 Office 文件上](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)。  

### <a name="actions-panes-and-custom-task-panes"></a>執行窗格和自訂工作窗格  
 執行窗格或自訂工作窗格具有焦點，當您存取控制項，您會存取 Windows Form 應用程式上的控制項的方式相同。 [動作] 窗格和文件之間移動游標，您可以按**F6**。  

 如需有關執行窗格和自訂工作窗格的詳細資訊，請參閱[執行窗格概觀](../vsto/actions-pane-overview.md)和[自訂工作窗格](../vsto/custom-task-panes.md)。  

### <a name="display-modes"></a>顯示模式  
 Visual Studio 有與顯示模式相關的下列限制：  

-   當您將文件的縮放設定變更為 100%以外的任何項目時，會停用的 Word 文件或 Excel 工作表上的控制項。  

-   **新專案**對話方塊如果未顯示控制項正確使用者變更電腦的協助工具選項，以**使用高對比**。  

 您可以使用 [放大鏡]，以克服這些限制。 [放大鏡] 是顯示公用程式建立個別的視窗以顯示螢幕的放的大部分的 Windows。  

## <a name="see-also"></a>另請參閱  
 [開發 Office 方案](../vsto/developing-office-solutions.md)   
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [殘障人士的協助工具](/visualstudio/ide/reference/accessibility-for-people-with-disabilities)   
 [Visual Studio 的協助工具功能](/visualstudio/ide/reference/accessibility-features-of-visual-studio)  
