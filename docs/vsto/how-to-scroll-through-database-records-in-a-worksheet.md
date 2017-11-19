---
title: "如何： 在工作表中的資料庫記錄捲動 |Microsoft 文件"
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
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
- worksheets [Office development in Visual Studio], scrolling records
ms.assetid: aea4c86c-9d6d-47dd-8977-066e21945dab
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 78ccd24a262863a4d6f844d624ef9996d09d568f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>如何：在工作表中捲動資料庫記錄
  下列程序示範如何使用設計工具，顯示在控制項，可讓使用者捲動瀏覽的所有記錄在 Microsoft Office Excel 工作表，從資料庫資料表的單一欄位。  
  
 只有在文件層級專案中，您可以使用設計工具。 不過，您也可以加入控制項，並將其繫結至資料以程式設計方式在執行階段。 如需詳細資訊，請參閱[逐步解說： 簡單資料繫結在 VSTO 增益集專案](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
### <a name="to-scroll-through-database-records-in-a-worksheet"></a>捲動資料庫記錄中工作表  
  
1.  Visual Studio 中開啟 Excel 應用程式專案。  
  
2.  開啟**資料來源**視窗，並從資料庫建立資料來源。 如需詳細資訊，請參閱[加入新連接](../data-tools/add-new-connections.md)。  
  
3.  展開包含您想要顯示，資料的資料表，並選取特定的資料行。  
  
4.  開啟的控制項，然後選取清單**NamedRange**。  
  
5.  拖曳<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項拖曳至想要顯示資料的儲存格。  
  
6.  從**Windows Form**  索引標籤**工具箱**，新增<xref:System.Windows.Forms.BindingNavigator>控制項加入工作表中，並設定您想要使用的控制項。 如需詳細資訊，請參閱[BindingNavigator 控制項概觀 &#40;Windows Form &#41;](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).  
  
## <a name="see-also"></a>另請參閱  
 [將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  