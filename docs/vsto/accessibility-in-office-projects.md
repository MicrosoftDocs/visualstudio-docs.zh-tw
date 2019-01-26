---
title: Office 專案中的協助工具
ms.date: 02/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, accessibility
- shortcut keys [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], shortcut keys
- accessibility [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 99deac9a1a6587d345d288123029a5e3dde4308b
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865849"
---
# <a name="accessibility-in-office-projects"></a>Office 專案中的協助工具

Microsoft Visual Studio 和 Microsoft Office 包含許多協助工具功能可讓您建置符合標準的協助工具需求的自訂解決方案。 Microsoft 會發佈在網站上的協助工具的指導方針。 如需詳細資訊，請參閱 <<c0> [ 協助工具網站](http://go.microsoft.com/fwlink/?LinkID=37113)。

在大部分情況下，Visual Studio 中的 Office 專案會符合您可以將它設定為讓您的解決方案可存取的協助工具標準或公開屬性。 不過，有一些具有有限的協助工具的功能。

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="accessibility-at-design-time"></a>在設計階段的協助工具

### <a name="use-shortcut-keys-in-document-level-projects"></a>在文件層級專案中使用快速鍵
 在 Visual Studio 中開啟 Microsoft Office Word 文件或 Microsoft Office Excel 活頁簿時，一次只有一個應用程式接收快顯命令。 根據預設，Visual Studio 會接收所有捷徑命令，但可讓 Word 或 Excel 文件藉由選取具有焦點時，接收它們**動態鍵盤配置**上**鍵盤設定**頁面**選項** 對話方塊。 如需詳細資訊，請參閱 < [Microsoft Office Word 鍵盤、 Microsoft Office 鍵盤設定、 [選項] 對話方塊](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)和[Microsoft Office Excel 鍵盤、 Microsoft Office 鍵盤設定、 [選項] 對話方塊中](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).

### <a name="display-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>文件層級專案中的功能區顯示快速鍵
 在 Visual Studio 中開啟 Word 文件或 Excel 活頁簿時，您無法按下**Alt**若要檢視的索引標籤和控制項的功能區上的快顯金鑰的金鑰。 若要檢視的鍵盤快速鍵，文件或活頁簿設計工具中開啟時，執行下列步驟。

#### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>若要檢視設計工具中的功能區索引標籤和控制項的快速鍵

1.  在 Visual Studio 中，在**工具**功能表上，按一下**選項**。

2.  依序展開**Office Tools**節點，然後選取**Microsoft Office Excel 鍵盤**或是**Microsoft Office Word 鍵盤**視需要。

3.  選取 **動態鍵盤配置**。

     此時會出現訊息指出您必須重新啟動 Visual Studio，變更才會生效。

4.  按一下 [確定 **Deploying Office Solutions**]。

5.  重新啟動 Visual Studio，並重新開啟您的專案。

6.  開啟您專案的文件或活頁簿設計工具。

7.  按下**F6**功能區顯示的快速鍵。

## <a name="accessibility-at-runtime"></a>在執行階段的協助工具

### <a name="windows-forms-controls-on-office-documents"></a>Office 文件上的 Windows Form 控制項
 Windows Form 控制項中公開協助工具屬性，以提供給協助工具輔助，例如螢幕助讀程式控制項的相關資訊。 您可以利用這些協助工具屬性的文件層級自訂中的 Office 文件的控制項時。 如需詳細資訊，請參閱 <<c0> [ 提供 Windows Form 上控制項的協助工具資訊](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form)。

 不過，有一些協助工具限制在執行階段上的 Excel 活頁簿或 Word 文件裝載 Windows Form 控制項時：

- 您不能到另一個索引標籤控制項。

- 當您將文件的縮放設定變更為 100%以外的任何項目時，會停用文件上的控制項。

  如需限制的文件上的 Windows Form 控制項的資訊，請參閱[Office 文件上的限制的 Windows Form 控制項](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)。

### <a name="actions-panes-and-custom-task-panes"></a>執行窗格和自訂工作窗格
 執行窗格或自訂工作窗格具有焦點，當您存取控制項相同的方式存取的 Windows Forms 應用程式上的控制項。 將游標和之間移動動作 窗格中的文件，您可以按下**F6**。

 如需有關執行窗格和自訂工作窗格的詳細資訊，請參閱 <<c0> [ 執行窗格概觀](../vsto/actions-pane-overview.md)並[自訂工作窗格](../vsto/custom-task-panes.md)。

### <a name="display-modes"></a>顯示模式

Visual Studio 有與顯示模式相關的下列限制：

- 當您將文件的縮放設定變更為 100%以外的任何項目時，會停用 Word 文件或 Excel 工作表上的控制項。

- **新的專案** 對話方塊不會顯示控制項正確地如果使用者變更電腦的協助工具選項**使用高對比**。

若要克服這些限制，您可以使用 [放大鏡]。 [放大鏡] 是顯示公用程式建立個別的視窗以顯示螢幕的放的大部分的 Windows。

## <a name="see-also"></a>另請參閱

- [開發 Office 方案](../vsto/developing-office-solutions.md)
- [Office 文件上的控制項](../vsto/controls-on-office-documents.md)
- [殘障人士的協助工具](../ide/reference/accessibility-for-people-with-disabilities.md)
- [Visual Studio 的協助工具功能](../ide/reference/accessibility-features-of-visual-studio.md)