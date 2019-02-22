---
title: HOW TO：捲動工作表中的資料庫記錄
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 7facc5a70b603b016bbafd207650caaef05027fa
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56600242"
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>HOW TO：捲動工作表中的資料庫記錄
  下列程序示範如何使用設計工具來顯示控制項，可讓使用者以捲動所有記錄在 Microsoft Office Excel 工作表，從資料庫資料表的單一欄位。

 您可以使用設計工具只能在文件層級專案中。 不過，您也可以新增控制項並繫結至資料，以程式設計方式在執行階段。 如需詳細資訊，請參閱[逐步解說：在 VSTO 增益集專案中的簡單資料繫結](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="to-scroll-through-database-records-in-a-worksheet"></a>捲動工作表中的資料庫記錄

1.  Visual Studio 中開啟 Excel 應用程式專案。

2.  開啟**Zdroje dat**視窗，並從資料庫建立資料來源。 如需詳細資訊，請參閱 <<c0> [ 新增連線](../data-tools/add-new-connections.md)。

3.  展開包含您想要顯示，資料的資料表，然後選取特定的資料行。

4.  開啟清單控制項，然後選取**NamedRange**。

5.  拖曳<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項拖曳至您想要顯示資料的儲存格。

6.  從**Windows Forms**索引標籤**工具箱**，新增<xref:System.Windows.Forms.BindingNavigator>控制項加入您的工作表，並設定您想要使用的控制項。 如需詳細資訊，請參閱 < [BindingNavigator 控制項概觀&#40;Windows Forms&#41;](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms)。

## <a name="see-also"></a>另請參閱
- [資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
