---
title: Office 專案中的協助工具
description: 瞭解 Microsoft Office 專案如何包含許多協助工具功能，可讓您建立符合標準協助工具需求的自訂解決方案。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4021517aa296f3c1e6355b82260b00590181f4cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955147"
---
# <a name="accessibility-in-office-projects"></a>Office 專案中的協助工具

Microsoft Visual Studio 和 Microsoft Office 包含許多協助工具功能，可讓您建立符合標準協助工具需求的自訂解決方案。 Microsoft 會發佈 Web 協助工具的指導方針。 如需詳細資訊，請參閱 [協助工具網站](https://www.microsoft.com/accessibility/)。

在大多數情況下，Visual Studio 中的 Office 專案會符合協助工具標準，或公開您可以設定的屬性，讓您的解決方案可供存取。 不過，某些功能的存取範圍有限。

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="accessibility-at-design-time"></a>設計階段的協助工具

### <a name="use-shortcut-keys-in-document-level-projects"></a>在檔層級專案中使用快速鍵
 當 Microsoft Office Word 檔或 Microsoft Office Excel 活頁簿在 Visual Studio 中開啟時，一次只有一個應用程式會收到快速鍵命令。 根據預設，Visual Studio 會接收所有快速鍵命令，但是您可以在檔具有焦點時，在 [**選項**] 對話方塊的 [**鍵盤設定**] 頁面上選取 [**動態鍵盤** 佈局]，讓 Word 或 Excel 接收它們。 如需詳細資訊，請參閱 [Microsoft Office Word 鍵盤、Microsoft Office 鍵盤設定、選項對話方塊](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) 和 [Microsoft Office Excel 鍵盤、Microsoft Office 鍵盤設定、選項對話方塊](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)。

### <a name="display-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>在檔層級專案中顯示功能區的快速鍵
 在 Visual Studio 中開啟 Word 檔或 Excel 活頁簿時，您不能按 **Alt** 鍵來查看功能區上索引標籤和控制項的快速鍵。 若要在設計工具中開啟檔或活頁簿時查看快速鍵，請執行下列步驟。

#### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>若要在設計工具中查看功能區索引標籤和控制項的快速鍵

1. 在 Visual Studio 中，按一下 [ **工具** ] 功能表上的 [ **選項**]。

2. 展開 [ **Office 工具** ] 節點，然後視需要選取 [ **Microsoft Office Excel 鍵盤** ] 或 [ **Microsoft Office Word 鍵盤**]。

3. 選取 [ **動態鍵盤** 佈局]。

     此時會出現一則訊息，指出您必須重新開機 Visual Studio，變更才會生效。

4. 按一下 [確定]  。

5. 重新開機 Visual Studio，然後重新開啟您的專案。

6. 開啟專案的檔或活頁簿設計工具。

7. 按 **F6** 鍵可顯示功能區的快速鍵。

## <a name="accessibility-at-run-time"></a>執行時間的協助工具

### <a name="windows-forms-controls-on-office-documents"></a>Office 檔上的 Windows Forms 控制項
 Windows Forms 控制項會公開協助工具屬性，將控制項的相關資訊提供給協助工具輔助，例如螢幕讀取器。 當控制項位於檔層級自訂中的 Office 檔時，您可以利用這些協助工具屬性。 如需詳細資訊，請參閱為 [Windows Form 上的控制項提供協助工具資訊](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form)。

 不過，當 Windows Forms 控制項裝載在 Excel 活頁簿或 Word 檔上時，執行時間會有一些協助工具限制：

- 您無法從一個控制項定位至另一個控制項。

- 當您將檔的縮放設定變更為100% 以外的任何值時，就會停用檔上的控制項。

  如需有關檔上 Windows Forms 控制項限制的詳細資訊，請參閱 [Office 檔上 Windows Forms 控制項的限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)。

### <a name="actions-panes-and-custom-task-panes"></a>動作窗格和自訂工作窗格
 當 [執行] 窗格或自訂工作窗格具有焦點時，您以存取 Windows Forms 應用程式之控制項的相同方式來存取控制項。 若要將游標移到 [動作] 窗格和檔之間，您可以按 **F6**。

 如需執行窗格和自訂工作窗格的詳細資訊，請參閱執行 [窗格總覽](../vsto/actions-pane-overview.md) 和 [自訂](../vsto/custom-task-panes.md)工作窗格。

### <a name="display-modes"></a>顯示模式

Visual Studio 與顯示模式有下列限制：

- 當您將檔的縮放設定變更為100% 以外的任何值時，Word 檔或 Excel 工作表上的控制項將會停用。

- 如果使用者變更電腦的協助工具選項來 **使用高對比**，[**新增專案**] 對話方塊就不會正確地顯示控制項。

您可以使用放大鏡來克服這些限制。 [放大鏡] 是 Windows 中的顯示公用程式，會建立顯示幕幕放大部分的個別視窗。

## <a name="see-also"></a>另請參閱

- [開發 Office 方案](../vsto/developing-office-solutions.md)
- [Office 檔上的控制項](../vsto/controls-on-office-documents.md)
- [殘障人士的協助工具](../ide/reference/accessibility-features-of-visual-studio.md)
- [Visual Studio 的協助工具功能](../ide/reference/accessibility-features-of-visual-studio.md)