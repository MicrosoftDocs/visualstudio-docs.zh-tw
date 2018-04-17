---
title: 如何： 以程式設計方式顯示工作表註解 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, comments
- comments, worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4f7ec00b58358fb51331a40ed246e4205c206323
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-display-worksheet-comments"></a>如何：以程式設計方式顯示工作表註解
  您可以透過程式設計方式，顯示及隱藏 Microsoft Office Excel 工作表中的註解。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-display-all-comments-on-a-worksheet-in-a-document-level-customization"></a>在文件層級自訂中，顯示工作表上的所有註解  
  
1.  如果您想要顯示註解，請將 <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> 屬性設定為 **true** ；否則設定為 **false**。 這個程式碼必須放置在工作表類別中，而不是 `ThisWorkbook` 類別中。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#31)]  
  
### <a name="to-display-all-comments-on-a-worksheet-in-an-application-level-vsto-add-in"></a>在應用程式層級 VSTO 增益集中，顯示工作表上的所有註解  
  
1.  如果您想要顯示註解，請將 <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> 屬性設定為 **true** ；否則設定為 **false**。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#21)]  
  
## <a name="see-also"></a>另請參閱  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何： 以程式設計方式加入和刪除工作表註解](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)  
  
  