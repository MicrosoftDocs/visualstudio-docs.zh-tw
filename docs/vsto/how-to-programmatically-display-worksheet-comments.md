---
title: 如何：以程式設計方式顯示工作表批註
description: 瞭解如何在檔層級或應用層級，以程式設計方式顯示和隱藏 Microsoft Excel 工作表中的批註。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: af327a6756189c73f80f624205451274abf19264
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828666"
---
# <a name="how-to-programmatically-display-worksheet-comments"></a>如何：以程式設計方式顯示工作表批註
  您可以透過程式設計方式，顯示及隱藏 Microsoft Office Excel 工作表中的註解。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-display-all-comments-on-a-worksheet-in-a-document-level-customization"></a>在文件層級自訂中，顯示工作表上的所有註解

1. 如果您想要顯示註解，請將 <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> 屬性設定為 **true** ；否則設定為 **false**。 這個程式碼必須放置在工作表類別中，而不是 `ThisWorkbook` 類別中。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet31":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet31":::

## <a name="to-display-all-comments-on-a-worksheet-in-an-application-level-vsto-add-in"></a>在應用程式層級 VSTO 增益集中，顯示工作表上的所有註解

1. 如果您想要顯示註解，請將 <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> 屬性設定為 **true** ；否則設定為 **false**。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet21":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet21":::

## <a name="see-also"></a>另請參閱
- [使用工作表](../vsto/working-with-worksheets.md)
- [如何：以程式設計方式新增及刪除工作表批註](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
