---
title: "如何： 以程式設計方式在工作表儲存格中顯示字串 |Microsoft 文件"
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
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4a76d2588ec07c461794381a2edd502d367be274
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>如何：以程式設計方式在工作表儲存格中顯示字串
  此範例示範如何以程式設計方式在資料格中顯示文字。 若要在資料格中顯示文字，請使用<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項或原生 Excel 範圍物件。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>使用 NamedRange 控制項  
 這個範例會使用<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項，名為`message`。 必須加入文件層級自訂在設計階段加入控制項。 下列程式碼必須放置在工作表類別中，不在`ThisWorkbook`類別。  
  
#### <a name="to-display-text-in-a-namedrange-control"></a>NamedRange 控制項中顯示文字  
  
1.  值設定<xref:Microsoft.Office.Tools.Excel.NamedRange>控制權傳輸至**Hello World**。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]  
  
## <a name="using-a-native-excel-range"></a>使用原生 Excel 範圍  
 下列程式碼以程式設計方式建立新的範圍，然後將值指派給它。  
  
#### <a name="to-display-text-in-an-excel-range"></a>在 Excel 範圍中顯示文字  
  
1.  擷取的資料格範圍**A1**上`Sheet1`並將值設定為**Hello World**。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]  
  
## <a name="see-also"></a>請參閱  
 [逐步解說： 收集資料，使用 Windows Form](../vsto/walkthrough-collecting-data-using-a-windows-form.md)   
 [Office 方案疑難排解](../vsto/troubleshooting-office-solutions.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)   
 [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  