---
title: 如何： 列印時隱藏工作表上的控制項 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4d02d823e707054fd17a5f3f892db41258b08081
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>如何：列印時隱藏工作表的控制項
  當您列印 Windows Form 控制項的 Microsoft Office Excel 文件時，控制項也會顯示在列印的工作表上。 列印工作表時，您可以隱藏控制項。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  如果您隱藏控制項，顯示資料，例如<xref:Microsoft.Office.Tools.Excel.Controls.TextBox>，控制項中的資料不會顯示在列印的工作表上。  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
### <a name="to-hide-controls-when-a-worksheet-is-printed"></a>若要隱藏工作表時的控制項列印  
  
1.  建立或開啟 Visual Studio 中的 Excel 專案，並確認**Sheet1**會顯示在設計工具中。 建立專案的詳細資訊，請參閱[How to： 建立 Visual Studio 中的 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  從**通用控制項** 索引標籤**工具箱**，拖曳<xref:Microsoft.Office.Tools.Excel.Controls.Button>控制權傳輸至儲存格上`Sheet1`。  
  
3.  在**屬性**視窗中，將<xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A>屬性**False**。  
  
## <a name="see-also"></a>另請參閱  
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [Windows Form 控制項，在 Office 文件概觀](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [如何： 將 Windows Form 控制項加入 Office 文件](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [如何：在工作表儲存格中調整控制項的大小](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
  
  