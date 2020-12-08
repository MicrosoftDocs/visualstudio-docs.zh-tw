---
title: 如何：以程式設計方式將資料列和資料行加入至 Word 資料表
description: 瞭解如何使用資料列物件的 Add 方法，將資料列加入至資料表。 您也可以使用 Columns 物件的 Add 方法來加入資料行。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- rows [Office development in Visual Studio], adding to Word tables
- tables [Office development in Visual Studio], adding rows and columns
- columns [Office development in Visual Studio], adding to Word tables
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 10154033c23cccc134752afb7f8b1e9c67099671
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846359"
---
# <a name="how-to-programmatically-add-rows-and-columns-to-word-tables"></a>如何：以程式設計方式將資料列和資料行加入至 Word 資料表
  在 Microsoft Office Word 表格中，儲存格會組織成資料列和資料行。 您可以使用 <xref:Microsoft.Office.Interop.Word.Rows> 物件的 <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> 方法新增資料表的資料列，以及使用 <xref:Microsoft.Office.Interop.Word.Columns> 物件的 <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> 方法來新增資料行。

 [!INCLUDE[appliesto_wdalldocapp](includes/appliesto-wdalldocapp-md.md)]

## <a name="document-level-customization-examples"></a>檔層級自訂範例
 下列程式碼範例可以用於文件層級自訂。 若要使用這些範例，請從專案的 `ThisDocument` 類別中執行它們。 這些範例假設與您自訂相關聯的文件已經有至少一張資料表。

> [!IMPORTANT]
> 只有在使用下列任何專案範本建立的專案中，才能執行此程式碼：
>
> - Word 2013 文件
> - Word 2013 範本
> - Word 2010 文件
> - Word 2010 範本
>
>   如果您想要在任何其他類型的專案中執行這項工作，您必須將參考加入至 node.js 元件，然後必須使用該元件 **中的類別** ，將資料列和資料行加入至資料表。 如需詳細資訊，請參閱 [如何：透過主要 interop 元件以 Office 應用程式為目標](how-to-target-office-applications-through-primary-interop-assemblies.md) ，以及 [Word 2010 主要 interop 元件參考](office-primary-interop-assemblies.md)。

### <a name="to-add-a-row-to-a-table"></a>在資料表中新增群組

1. 使用 <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> 方法，以在資料表中新增資料列。

     [!code-vb[Trin_VstcoreWordAutomation#95](codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomation#95](codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#95)]

### <a name="to-add-a-column-to-a-table"></a>在資料表中新增資料行

1. 使用 <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> 方法，然後使用 <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> 方法將所有資料行都設為相同寬度。

     [!code-vb[Trin_VstcoreWordAutomation#96](codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomation#96](codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#96)]

## <a name="vsto-add-in-examples"></a>VSTO 增益集範例
 下列程式碼範例可以用於 VSTO 增益集。 若要使用這些範例，請從專案的 `ThisAddIn` 類別中執行它們。 這些範例假設使用中文件已經有至少一張資料表。

> [!IMPORTANT]
> 只有在使用 Word VSTO 增益集範本建立的專案中，才能執行此程式碼。
>
> 如果您想要在任何其他類型的專案中執行這項工作，您必須將參考加入至 node.js 元件，然後必須使用該元件 **中的類別** ，將資料列和資料行加入至資料表。 如需詳細資訊，請參閱 [如何：透過主要 interop 元件以 Office 應用程式為目標](how-to-target-office-applications-through-primary-interop-assemblies.md) ，以及 [Word 2010 主要 interop 元件參考](office-primary-interop-assemblies.md)。

### <a name="to-add-a-row-to-a-table"></a>在資料表中新增群組

1. 使用 <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> 方法，以在資料表中新增資料列。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#95)]

### <a name="to-add-a-column-to-a-table"></a>在資料表中新增資料行

1. 使用 <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> 方法，然後使用 <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> 方法將所有資料行都設為相同寬度。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#96)]

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式建立 Word 表格](how-to-programmatically-create-word-tables.md)
- [如何：以程式設計方式在 Word 表格的儲存格中加入文字和格式](how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [如何：以程式設計方式將文件屬性填入 Word 表格](how-to-programmatically-populate-word-tables-with-document-properties.md)
