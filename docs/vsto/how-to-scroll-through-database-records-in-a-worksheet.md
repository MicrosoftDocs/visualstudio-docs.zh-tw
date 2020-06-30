---
title: 如何：在工作表中滾動資料庫記錄
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
- worksheets [Office development in Visual Studio], scrolling records
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8127a5f61e292fb777be4854796535bbe01226aa
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545791"
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>如何：在工作表中滾動資料庫記錄
  下列程式會示範如何使用設計工具，從 Microsoft Office Excel 工作表中的資料庫資料表顯示單一欄位，並提供可讓使用者在所有記錄中進行滾動的控制項。

 您只能在檔層級專案中使用設計工具。 不過，您也可以加入控制項，並在執行時間以程式設計方式將它們系結至資料。 如需詳細資訊，請參閱[逐步解說： VSTO 增益集專案中的簡單資料](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)系結。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="to-scroll-through-database-records-in-a-worksheet"></a>若要在工作表中流覽資料庫記錄

1. 在 Visual Studio 中開啟 Excel 應用程式專案。

2. 開啟 [**資料來源**] 視窗，並從資料庫建立資料來源。 如需詳細資訊，請參閱[新增連接](../data-tools/add-new-connections.md)。

3. 展開包含您要顯示之資料的資料表，然後選取特定的資料行。

4. 開啟控制項清單，然後選取 [ **NamedRange**]。

5. 將控制項拖曳至 <xref:Microsoft.Office.Tools.Excel.NamedRange> 您想要顯示資料的儲存格。

6. 從 [**工具箱**] 的 [ **Windows Forms** ] 索引標籤中，將 <xref:System.Windows.Forms.BindingNavigator> 控制項新增至您的工作表，然後設定您想要使用的控制項。 如需詳細資訊，請參閱[BindingNavigator 控制項總覽 &#40;Windows Forms&#41;](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms)。

## <a name="see-also"></a>另請參閱
- [將資料系結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
