---
title: 如何：以程式設計方式顯示工作表批註
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, comments
- comments, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0fc84e2726cd7a70b8fc59b0f1ac2b3377f9c4af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543360"
---
# <a name="how-to-programmatically-display-worksheet-comments"></a>如何：以程式設計方式顯示工作表批註
  您可以透過程式設計方式，顯示及隱藏 Microsoft Office Excel 工作表中的註解。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-display-all-comments-on-a-worksheet-in-a-document-level-customization"></a>在文件層級自訂中，顯示工作表上的所有註解

1. 如果您想要顯示註解，請將 <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> 屬性設定為 **true** ；否則設定為 **false**。 這個程式碼必須放置在工作表類別中，而不是 `ThisWorkbook` 類別中。

     [!code-csharp[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#31)]

## <a name="to-display-all-comments-on-a-worksheet-in-an-application-level-vsto-add-in"></a>在應用程式層級 VSTO 增益集中，顯示工作表上的所有註解

1. 如果您想要顯示註解，請將 <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> 屬性設定為 **true** ；否則設定為 **false**。

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#21)]

## <a name="see-also"></a>另請參閱
- [使用工作表](../vsto/working-with-worksheets.md)
- [如何：以程式設計方式新增及刪除工作表批註](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
