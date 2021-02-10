---
title: 如何：以程式設計方式保護工作表
description: 瞭解如何使用 Microsoft Excel 中的保護功能，防止使用者和程式碼修改工作表中的物件。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- protection, adding to worksheets
- documents [Office development in Visual Studio], document protection
- document protection, adding to worksheets
- worksheets, protecting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 92ded3d8320f58bdd200f3892dc40c7a915c502e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963818"
---
# <a name="how-to-programmatically-protect-worksheets"></a>如何：以程式設計方式保護工作表
  Microsoft Office Excel 中的保護功能有助於防止使用者和程式碼修改工作表中的物件。 根據預設，開啟保護之後所有的儲存格都會鎖定。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 使用文件層級自訂時，您可以使用 Excel 設計工具保護工作表。 您也可以用程式設計的方式，在任何專案類型的執行階段中保護工作表。

> [!NOTE]
> 您無法將 Windows Form 控制項加入受保護的工作表區域。

## <a name="use-the-designer"></a>使用設計工具

### <a name="to-protect-a-worksheet-in-the-designer"></a>若要用設計工具保護工作表

1. 在 [**審核**] 索引標籤的 [**變更**] 群組中，按一下 [**保護工作表**]。

    [ **保護工作表** ] 對話方塊隨即出現。 您可以設定密碼，並且選擇性地指定允許使用者對工作表執行某些動作 (例如格式化儲存格或插入列)。

   您也可以允許使用者在受保護的工作表中編輯特定的範圍。

### <a name="to-allow-editing-in-specific-ranges"></a>若要允許在特定範圍中進行編輯

1. 在 [**審核**] 索引標籤的 [**變更**] 群組中，按一下 [**允許使用者編輯範圍**]。

     [ **允許使用者編輯範圍** ] 對話方塊隨即出現。 您可以指定需要使用密碼才能解除鎖定的範圍，以及不需要密碼就可以編輯範圍的使用者。

## <a name="use-code-at-run-time"></a>在執行時間使用程式碼
 下列程式碼會設定密碼 (使用變數 getPasswordFromUser，它含有從使用者取得的密碼)，並且只允許排序。

### <a name="to-protect-a-worksheet-by-using-code-in-a-document-level-customization"></a>若要在文件層級自訂中使用程式碼保護工作表

1. 呼叫工作表的 <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> 方法。 這個範例會假設您是使用名為 `Sheet1`的工作表。

     [!code-csharp[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#27)]

### <a name="to-protect-a-worksheet-by-using-code-in-a-vsto-add-in"></a>若要在 VSTO 增益集中使用程式碼保護工作表

1. 呼叫使用中工作表的 <xref:Microsoft.Office.Interop.Excel._Worksheet.Protect%2A> 方法。

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#17)]

## <a name="see-also"></a>另請參閱
- [使用工作表](../vsto/working-with-worksheets.md)
- [如何：以程式設計方式移除工作表的保護](../vsto/how-to-programmatically-remove-protection-from-worksheets.md)
- [如何：以程式設計方式保護活頁簿](../vsto/how-to-programmatically-protect-workbooks.md)
- [如何：以程式設計方式隱藏工作表](../vsto/how-to-programmatically-hide-worksheets.md)
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
- [工作表主專案](../vsto/worksheet-host-item.md)
- [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
