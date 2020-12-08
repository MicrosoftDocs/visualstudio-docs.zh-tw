---
title: 如何：列印時隱藏工作表上的控制項
description: 瞭解在列印包含 Windows Forms 控制項的 Microsoft Office Excel 工作表時，您可以隱藏控制項。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: acc90986dd394e69de12893aac01e0a4f662b1a3
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846489"
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>如何：列印時隱藏工作表上的控制項
  當您列印包含 Windows Forms 控制項 Microsoft Office Excel 檔時，會在列印的工作表上顯示這些控制項。 列印工作表時，您可以隱藏控制項。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> 如果您隱藏顯示資料的控制項（例如 <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> ），則在列印的工作表上將看不到控制項中的資料。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="to-hide-controls-when-a-worksheet-is-printed"></a>若要在列印工作表時隱藏控制項

1. 在 Visual Studio 中建立或開啟 Excel 專案，並確認 **Sheet1** 顯示于設計工具中。 如需建立專案的詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

2. 從 [**工具箱**] 的 [**通用控制項**] 索引標籤，將 <xref:Microsoft.Office.Tools.Excel.Controls.Button> 控制項拖曳至上的儲存格 `Sheet1` 。

3. 在 [ **屬性** ] 視窗中，將 <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> 屬性設定為 **False**。

## <a name="see-also"></a>另請參閱
- [Office 檔上的控制項](../vsto/controls-on-office-documents.md)
- [Office 檔上的 Windows Forms 控制項總覽](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [如何：將 Windows Forms 控制項新增至 Office 檔](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [如何：調整工作表儲存格內的控制項大小](../vsto/how-to-resize-controls-within-worksheet-cells.md)
