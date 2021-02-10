---
title: 如何：在工作表中滾動資料庫記錄
description: 瞭解如何使用設計工具，在 Microsoft Excel 工作表中顯示資料庫資料表的單一欄位
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 29e6d4decf3d314654c4417f71bd7a2bad358b95
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949723"
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>如何：在工作表中滾動資料庫記錄
  下列程式示範如何使用設計工具，在 Microsoft Office Excel 工作表中顯示資料庫資料表的單一欄位，以及可讓使用者滾動所有記錄的控制項。

 您只可以在檔層級專案中使用設計工具。 不過，您也可以在執行時間以程式設計方式加入控制項，並將其系結至資料。 如需詳細資訊，請參閱 [逐步解說： VSTO 增益集專案中的簡單資料](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)系結。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="to-scroll-through-database-records-in-a-worksheet"></a>若要在工作表中滾動資料庫記錄

1. 在 Visual Studio 中開啟 Excel 應用程式專案。

2. 開啟 [ **資料來源** ] 視窗，並從資料庫建立資料來源。 如需詳細資訊，請參閱 [加入新的連接](../data-tools/add-new-connections.md)。

3. 展開包含您想要顯示之資料的資料表，然後選取特定的資料行。

4. 開啟控制項清單，然後選取 [ **NamedRange**]。

5. 將控制項拖曳至 <xref:Microsoft.Office.Tools.Excel.NamedRange> 您想要顯示資料的資料格上。

6. 從 [**工具箱**] 的 [ **Windows Forms** ] 索引標籤中，將 <xref:System.Windows.Forms.BindingNavigator> 控制項加入至您的工作表，並設定您要使用的控制項。 如需詳細資訊，請參閱 [BindingNavigator 控制項總覽 &#40;Windows Forms&#41;](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms)。

## <a name="see-also"></a>另請參閱
- [將資料系結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
